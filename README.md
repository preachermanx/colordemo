# Color Demo Example

For Digital Rebar Provision

To install the colordemo content pack, use the following command:

  `git clone https://github.com/digitalrebar/colordemo.git`
  `cd contents`
  `drpcli contents bundle ../colordemo-v1.yaml`

To inject/install it to a Digital Rebar Provision endpoint, use:

  `drpcli contents create ../colordemo-v1.yaml`

If you make changes to the local files (updates, edits, fixes, etc), and
want to update the already installed conent pack, rebundle the changes,
then update as follows:

  `# edit files as desired`
  `drpcli contents bundle ../colordemo-v2.yaml`
  `drpcli contents update colordemo ../colordemo-v2.yaml`

## Feature in Videos!

* Creating Content: https://youtu.be/79Y-3IOguZk
* Bundling: https://youtu.be/JUyzFNkLyZU

## Operating Colordemo

You must have a machine that is currently running an Agent ("runner-service");
the "Sledgehammer" (discovery) bootenv meets this criteria, or the
"runner-service" has been run on an installed OS.  Verify the agent is running
with "ps -ef | grep 'drpcli processjobs' | grep -v grep".

Add the "colordemo-example" profile to the machine, a cloned version of the
profile with your changes to the Params, or the bare params directly to
the machine.

Set the machine to the "colordemo" Workflow.  The "i" (information) column
should change to the set color and icon.  To rerun the workflow, you must
first clear the workflow (remove) the current "colordemo" workflow, then
re-set it on the machine.

## Which DRP Endpoint are you talking to?

Remember that the "drpcli" client tool by default connects to the address
and port specified as follows:

  `https://127.0.0.1:8092`

Make sure you set the Endpoint (and Username/Password if changed from defaults)
with the appropriate options.  Run "drpcli" by itself to get help output.

## Notes:

The contents bundle operation is very sensitve to errant/unexpected files
in the directory structure.  Anything that is NOT a meta file (eg a file
with ".__Something.meta" or a YAML file will be misinterpreted and an
error will occur on the bundle operation, like:

  `drp@pixie:./colordemo$ drpcli contents bundle colordemo-v1.yaml`
  `Error: Failed to load: No idea how to decode LICENSE into dr-provision-releases`

(".gitignore" will also similarly cause an error).  Insure your directory
is clean from errant hidden/dot files, things like "LICENSE", "README.md", etc.

For this reason, the "colordemo" contents have been moved in to the subdirectory
named "contents/".
