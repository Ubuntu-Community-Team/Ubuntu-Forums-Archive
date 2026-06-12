---
title: "Hide/Show a Panel with keyboard?"
date: 2008-08-03
forum: General Help
---

### Post by eshm on 2008-08-03
Does anybody know of a way to assign a keyboard shortcut to the hide/show feature of a panel?  I'm not sure if this is even possible, but I thought it would be worth asking here.

---

### Post by drs305 on 2008-08-03
It's not efficient, but here is a way to do it if you really want to:

You can edit your gconf settings for hide/unhide. For instance, to auto-hide the bottom panel, the CLI command is (0=false, 1=true):
```
gconftool-2 --type bool --set /apps/panel/toplevels/bottom_panel_screen0/auto_hide '1'
```

You could make a script and then use the metacity keybinds in gconf-editor to invoke that script with a key combination.
For example, to turn on the hide feature of the lower panel, make a script (don't forget to make it executable through your file browser or chmod a+x):
```
#!/bin/bash
gconftool-2 --type bool --set /apps/panel/toplevels/bottom_panel_screen0/auto_hide '1'
```

Open gconf-editor, then go to metacity/keybinding_commands, and for command_X (X being a number), enter "/home/*username*/path.to.script/hidebottompanel.sh"

Next go to metacity/global_keybindings, and set run_command_X to the key combination you want (e.g. <ALT>L.

You would have to repeat this with a different key to unhide the panel.

There may be other options in gconf's settings that might hide all panels, you'd just have to look around metacity's /apps/panel/ settings.

---

