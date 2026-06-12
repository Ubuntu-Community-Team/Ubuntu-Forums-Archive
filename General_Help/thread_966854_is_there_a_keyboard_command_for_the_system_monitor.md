---
title: "is there a keyboard command for the system monitor? (like win's ctrl+alt+del)"
date: 2008-11-01
forum: General Help
---

### Post by reinaldistic on 2008-11-01
is there a keyboard command for the system monitor? (like win's ctrl+alt+del)  but for ubuntu

---

### Post by editrix on 2008-11-02
In Kubuntu it's Control-Escape. Presumably the same for Ubuntu.

---

### Post by bryncoles on 2008-11-02
im not aware of a command existing by default, but i know you can set one. 

first, check the key combo you want to use isnt already assigned elsewhere by looking in system, preferences keyboard shortcuts. resolve any potential conflicts. 

then use synaptic package manager to install compiz advanced configuration manager.

then system->preferences->compizconfig advanced settings->general options->commands.

in the tab for 'commands' put in 'gnome-system-monitor' (without quotes). in the tab for keybindings, on the corresponding line, put the key combo you want to summon system monitor.

you can also set other keyboard shortcuts here!

you can also use 'gnome-system-monitor', or 'top' or 'sudo top' in the terminal.... (beware with any 'sudo' commands though, having admin tasks running can be hazardous, though 'top' is just a system monitor program so not dangerous...)

---

