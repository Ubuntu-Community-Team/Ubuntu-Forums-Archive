---
title: "Touchpad disabled on only ONE userid"
date: 2012-12-31
forum: Hardware
---

### Post by erlrodd on 2012-12-31
My touchpad is enabled using all the normal methods on my Samsung N150. However, on one userid, it does not work. The touchpad-indicator shows it disabled and the
"Enable Touchpad" feature of touchpad-indicator does nothing. On other userids,
the touchpad can be enabled and disabled.

This is independent of window manager. On other userids, touchpad works with
Unity or gnome. On my one userid, it works with neither. 

Ubuntu 12.04.

xinput list shows the touchpad on any userid, even the one where it does not work.

So what can be different in this userid?
.profile and .bashrc have pretty simple,normal stuff in them.

---

### Post by erlrodd on 2013-01-01
Found it:
1. Moved $HOME/config somewhere to save and then touchpad was OK.
2. greped files in .config and found "touchpad" only in .config/dconf/users
3. Made a script with all schemas from output of gsettings list-schemas
4. Script did
gsettings list-keys 
for every schema
5. Found in org.gnome.settings-daemon.peripherals.touchpad 
6. Used dconf-editor to change settings - touchpad was disabled,

REMAINING QUESTION
How did this ever get set? Might be left from the migration from 10.04?

---

