# HEMTT Usage
<pre>
Usage:
    hemtt <a href="/#/usage?id=init">init</a>
    hemtt <a href="/#/usage?id=create">create</a>
    hemtt <a href="/#/usage?id=addon">addon</a> &lt;name&gt;
    hemtt <a href="/#/usage?id=build">build</a> [--release] [--force] [--nowarn]
    hemtt <a href="/#/usage?id=update">update</a>
    hemtt (-h | --help)
    hemtt --version

Options:
    -f  --force          Overwrite target files
        --nowarn         Suppress armake2 warnings
    -h  --help           Show usage information and exit
        --version        Show version number and exit
</pre>
<hr/>

# init

Initialize a project file in the current directory. `init` is used when you have existing files or do not want to use the CBA structure.
<hr/>

# create

Create a new project using the CBA project structure. `create` should only be used inside an empty directory. The following structure will be generated.
<pre>
.
├── hemtt.json
└── <a href="https://github.com/synixebrett/HEMTT-Example/tree/master/addons">addons/</a>
    └── <a href="https://github.com/synixebrett/HEMTT-Example/tree/master/addons/main">main/</a>
        ├── <a href="https://github.com/synixebrett/HEMTT-Example/blob/master/addons/main/%24PBOPREFIX%24">$PBOPREFIX$</a>
        ├── <a href="https://github.com/synixebrett/HEMTT-Example/blob/master/addons/main/config.cpp">config.cpp</a>
        ├── <a href="https://github.com/synixebrett/HEMTT-Example/blob/master/addons/main/script_component.hpp">script_component.hpp</a>
        ├── <a href="https://github.com/synixebrett/HEMTT-Example/blob/master/addons/main/script_macros.hpp">script_macros.hpp</a>
        ├── <a href="https://github.com/synixebrett/HEMTT-Example/blob/master/addons/main/script_mod.hpp">script_mod.hpp</a>
        └── <a href="https://github.com/synixebrett/HEMTT-Example/blob/master/addons/main/script_version.hpp">script_version.hpp</a>
</pre>
<hr/>

# addon

Create a new addon folder. Requires a name to be used for the addon.

```
./hemtt addon common
```
<pre>
.
└── <a href="https://github.com/synixebrett/HEMTT-Example/tree/master/addons">addons/</a>
    └── <a href="https://github.com/synixebrett/HEMTT-Example/tree/master/addons/common">common</a>
        ├── <a href="https://github.com/synixebrett/HEMTT-Example/blob/master/addons/common/%24PBOPREFIX%24">$PBOPREFIX$</a>
        ├── <a href="https://github.com/synixebrett/HEMTT-Example/blob/master/addons/common/CfgEventHandlers.hpp">CfgEventHandlers.hpp</a>
        ├── <a href="https://github.com/synixebrett/HEMTT-Example/blob/master/addons/common/XEH_PREP.hpp">XEH_PREP.hpp</a>
        ├── <a href="https://github.com/synixebrett/HEMTT-Example/blob/master/addons/common/XEH_postInit.sqf">XEH_postInit.sqf</a>
        ├── <a href="https://github.com/synixebrett/HEMTT-Example/blob/master/addons/common/XEH_preInit.sqf">XEH_preInit.sqf</a>
        ├── <a href="https://github.com/synixebrett/HEMTT-Example/blob/master/addons/common/XEH_preStart.sqf">XEH_preStart.sqf</a>
        ├── <a href="https://github.com/synixebrett/HEMTT-Example/blob/master/addons/common/config.cpp">config.cpp</a>
        ├── <a href="https://github.com/synixebrett/HEMTT-Example/blob/master/addons/common/script_component.hpp">script_component.hpp</a>
        └── <a href="https://github.com/synixebrett/HEMTT-Example/tree/master/addons/common/functions">functions/</a>
            └── <a href="https://github.com/synixebrett/HEMTT-Example/blob/master/addons/common/functions/script_component.hpp">script_component.hpp</a>
</pre>
<hr>

# build
Build the project into PBO files. HEMTT will only build the files that have changed.

## Flags

### --nowarn
Hide warnings from the armake2 build process.

### --force -f
Remove existing built files before starting the next build.

### --release
Create and sign a release build of the project.

A `hemtt.json` file of 
```json
{
  "name": "Test Mod",
  "prefix": "TST",
  "author": "SynixeBrett",
  "files": [
    "mod.cpp"
  ]
}
```
would produce
<pre>
.
└── releases/
    └── 0.1.0.0/
        └── <a href="https://github.com/synixebrett/HEMTT-Example/tree/master/releases/0.1.0.0/%40TST">@TST/</a>
            ├── mod.cpp
            └── addons/
                ├── TST_common.pbo
                ├── TST_example.pbo
                └── TST_main.pbo
</pre>

This example is from the [HEMTT Example Project](https://github.com/synixebrett/HEMTT-Example)
<hr/>

# update

HEMTT will look for a more recent version online. If one is available you will be prompted to download the updated version.