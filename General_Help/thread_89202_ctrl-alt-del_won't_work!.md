---
title: "ctrl-alt-del won't work!"
date: 2005-11-12
forum: General Help
---

### Post by syons on 2005-11-12
Right after "**automatix**" installation and first execution, it did call upthe system monitor. But after reboot, it won't work. Does anyone have the same problem?

---

### Post by aysiu on 2005-11-12
You may have to remap the key sequence to be for System Monitor again. You can do this in Applications > System Tools > Configuration Editor > Apps > Metacity > Global Keybindings / Keybinding Commands. Make the keybinding command ```
gnome-system-monitor
``` and the keybindings ```
<Control><Alt>Delete
```

---

### Post by MetalMusicAddict on 2005-11-12
In a terminal type:
**gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_9 "<Control><Alt>Delete"**
Then:
**gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_9 "gnome-system-monitor"**

Works like a charm.

---

