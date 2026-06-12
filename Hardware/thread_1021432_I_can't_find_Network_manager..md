---
title: "I can't find Network manager."
date: 2008-12-25
forum: Hardware
---

### Post by Hemen on 2008-12-25
In Ubuntu i can't find Network manager. Somehow one day it wasn't there anymore O_O

How do i get i back?

---

### Post by taurus on 2008-12-25
See if you can reinstall it.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install network-manager-gnome
```

---

### Post by Ahadiel on 2008-12-25
If it's not showing up in your tray, try running:
```
nm-applet --sm-disable
```
Also check System => Preferences => Session and make sure it's there.

---

### Post by arlen on 2008-12-25
I am having the same problem. Here's the output:


```
arlen@turing:~$ nm-applet --sm-disable

** (nm-applet:10314): WARNING **: <WARN>  applet_dbus_manager_start_service(): Could not acquire the NetworkManagerUserSettings service as it is already taken.  Return: 3


(nm-applet:10314): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
```

---

### Post by lswb on 2008-12-25
Probably you have accidentally deleted the notification area from your panel. Right click on the panel where you would like to see the NM applet icon, select Add to Panel, then scroll down through the list and select Notification Area. If the NM icon doesn't show up right away, try Main Menu/System/Preferences/Sessions and make sure Network Manager has a checkmark in the Enabled column. If it still doesn't show up after closing the Sessions dialog, you may have to log out of gnome and back in again.

---

