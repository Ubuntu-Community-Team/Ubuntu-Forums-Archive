---
title: "[SOLVED] Launch $app with hotkey?"
date: 2008-11-09
forum: General Help
---

### Post by sci-fi guy on 2008-11-09
How can I assign a hotkey to launch an arbitrary application?
System>>Preferences>>Keyboard Shortcuts doesn't have what I need (I can use that to assign a hotkey to Firefox or a terminal window, but not much else), and I don't want to use Compiz.

---

### Post by kaibob on 2008-11-09
Load Gnome Configuration Editor and navigate to the following key:

/apps/metacity/keybinding_commands

Insert the command that will load the desired program after one of the numbered commands. 

Next, navigate to the following key:

/apps/metacity/global_keybindings

Insert the keyboard key value (e.g. <Alt>F2) after the numbered command used above.

---

### Post by easoukenka on 2008-11-09
[http://www.howtogeek.com/howto/ubuntu/assign-custom-shortcut-keys-on-ubuntu-linux/](http://www.howtogeek.com/howto/ubuntu/assign-custom-shortcut-keys-on-ubuntu-linux/)

maybe that will help

---

