---
title: "latest update broke network manager or....."
date: 2008-11-06
forum: General Help
---

### Post by phoenix_snake on 2008-11-06
Hi, alright so on 8.10 the last few updates have broken network manager for me or something anyway network manager doesn't start so I can't connect using eth0.

awesome, so network isn't reliable either?

---

### Post by phoenix_snake on 2008-11-07
bump

---

### Post by pelle.k on 2008-11-07
Allrighty then!
I guess you don't want to copy/paste from another computer, so lets try to get the connection going, and maybe update?

```
sudo ifconfig eth0 up
sudo dhclient eth0
```

To check if there was any errors loading the interface;
```
dmesg | grep -i eth
```

---

### Post by phoenix_snake on 2008-11-07
I just restarted the computer and amazingly the network connection has started to work but network manager still won't load :(

---

### Post by pelle.k on 2008-11-07
Aah, allright. So you have internet, but the applet (the icon in the notification area doesn't load?)
Try pasting the output of ```
nm-applet --sm-disable
``` here.

---

### Post by phoenix_snake on 2008-11-07
user@user-desktop:~$ nm-applet --sm-disable

** (nm-applet:5705): WARNING **: <WARN>  applet_dbus_manager_start_service(): Could not acquire the NetworkManagerUserSettings service as it is already taken.  Return: 3


(nm-applet:5705): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
user@user-desktop:~$ nm-applet

** (nm-applet:5706): WARNING **: <WARN>  applet_dbus_manager_start_service(): Could not acquire the NetworkManagerUserSettings service as it is already taken.  Return: 3


(nm-applet:5706): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
user@user-desktop:~$

---

### Post by phoenix_snake on 2008-11-07
any other info required?

---

### Post by pelle.k on 2008-11-07
Well, this is a nasty bug actually; [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/284596](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/284596)
It would seem the networkmanager (applet) thinks it cant start because it's open in another user session (even though that shouldn't be a problem either).

Your wired connection will continue to function though.
You may run "nm-connection-editor" to modify your connection instead.
If you only want a network monitor, add the "network monitor" applet in the gnome panel.
Sorry i couldn't be of more help.

---

### Post by phoenix_snake on 2008-11-08
> **pelle.k said:**
> Well, this is a nasty bug actually; [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/284596](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/284596)
It would seem the networkmanager (applet) thinks it cant start because it's open in another user session (even though that shouldn't be a problem either).

Your wired connection will continue to function though.
You may run "nm-connection-editor" to modify your connection instead.
If you only want a network monitor, add the "network monitor" applet in the gnome panel.
Sorry i couldn't be of more help.
another bug? how do they release an OS like this? thanks for the link though and now I do remember trying to switch users and see what happens....

---

