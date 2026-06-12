---
title: "Dell Studio Crashes. Something with D-bus, I think."
date: 2008-12-03
forum: Hardware
---

### Post by pah99 on 2008-12-03
Hi. I have a Dell Studio 1535 with 8.10 installed. This thing crashes on me every single day. I have looked into the System Log, and in particular the auth.log. When looking at it, the last thing mentioned before the crash is the following: 
Dec  3 20:58:07 pasha-laptop gdm[15026]: )gnome-keyring-daemon: couldn't lookup pkcs11 component setting: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified.

This error pops up a lot in this log. I have looked at that website but couldn't figure anything out.

So what happens is that I am online with my wifi, and then the screen locks up, sound locks up, no buttons on my keyboard work, and the only way to end it is a hard reboot. 
Any help is appreciated.

---

### Post by pah99 on 2008-12-03
Never Mind. I found another thread with this. Thanks

---

