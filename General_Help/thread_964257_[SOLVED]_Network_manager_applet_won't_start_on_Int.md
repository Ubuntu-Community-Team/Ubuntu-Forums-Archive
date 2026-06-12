---
title: "[SOLVED] Network manager applet won't start on Intrepid"
date: 2008-10-30
forum: General Help
---

### Post by wersdaluv on 2008-10-30
I'm on my fresh Intrepid now with my old configuration files (since I have a separate /home partition). Now, on my old user account, network manager wont start even if there's a "nm-applet --sm-disable" on my startup programs on gnome's session preferences.

There's no problem with network manager on a fresh user account, though.

Any idea? :)

---

### Post by wersdaluv on 2008-10-30
Rebooting did the magic :)

---

### Post by !nkubus on 2008-10-31
I have the same issue bur rebooting didn't do the trick :(

here is my network manager output when I run **nm-applet --sm-disable**:

** (nm-applet:3028): WARNING **: <WARN>  applet_dbus_manager_start_service(): Could not acquire the NetworkManagerUserSettings service as it is already taken.  Return: 3


(nm-applet:3028): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

---

### Post by lord_phantom on 2008-10-31
I did a fresh install of 8.10 (/home was also formated). The nm-applet disappeared after I changed my MAC address using /etc/network/interfaces.

---

### Post by conscious on 2008-10-31
See [http://ubuntuforums.org/showthread.php?t=956187](http://ubuntuforums.org/showthread.php?t=956187) and [https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/249404](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/249404).

Also, it seems that you can restore the applet with the following commands:
```
killall nm-applet
nm-applet --sm-disable
```

---

