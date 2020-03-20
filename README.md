# tutorial_ams_cds_ff_mpt

Open-source release of cds_ff_mpt workspace.

## Licensing

This library is licensed under the Apache-2.0 license.  See [here](LICENSE) for full text of the
Apache license.

# Setting up

1. Clone the repository.

2. In the workspace, update submodules:

```
git submodule update --init --recursive
```

The submodules and this repo itself are setup using ssh.  If for some reason you are unable to access external sources via ssh (firewall or access reasons) you can most likely setup ssh over the https port, as shown [here](https://help.github.com/en/github/authenticating-to-github/using-ssh-over-the-https-port)

3. Change various environment files in `skywater130/workspace_setup` to match your settings.
This will include the paths to tools found in the .bashrc file.

4. Setup environment:
```
source .bashrc
```

5. Compile pybag if you have OpenAccess source code:

```
cd BAG_framework/pybag
./run_test.sh
```

or obtain pre-compiled library from Blue Cheetah.

6. Create cds.lib file:
```
echo 'INCLUDE $BAG_WORK_DIR/cds.lib.core' > cds.lib
```


# Running example

1. To generate an inverter:

```
./run_bag.sh BAG_framework/run_scripts/gen_cell.py data/tutorial_ams/specs_gen/inv.yaml
```

2. To generate GDS/netlist file:

```
./run_bag.sh BAG_framework/run_scripts/gen_cell.py data/tutorial_ams/specs_gen/inv.yaml -raw
```

3. To run LVS on the generated GDS/netlist file:

```
./run_bag.sh BAG_framework/run_scripts/gen_cell.py data/tutorial_ams/specs_gen/inv.yaml -raw -v
```

An tristate-inverter, NAND2, NOR2 example are also provided, just change the YAML file path.  Look
at the files in the `data/tutorial_ams/specs_gen` for the names.

