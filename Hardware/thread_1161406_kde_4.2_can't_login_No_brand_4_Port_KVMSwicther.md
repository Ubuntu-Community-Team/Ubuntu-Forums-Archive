---
title: "kde 4.2: can't login: No brand 4 Port KVMSwicther?"
date: 2009-05-16
forum: Hardware
---

### Post by oddiofile on 2009-05-16
Fresh install of Kubuntu 9.04:

Looking at the tail of the log file, I see the only errors are related to my USB KVM switcher and the keyboard/mouse that are plugged into it.


Build Date: 09 April 2009  02:11:54AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@crested.buildd)
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat May 16 14:15:53 2009
(==) Using config file: "/etc/X11/xorg.conf"
(EE) Chicony USB Keyboard: Read error: No such device
(EE) Chicony USB Keyboard: Read error: No such device
(EE) PATEN USB HID Device: Read error: No such device
(EE) No brand 4 Port KVMSwicther: Read error: No such device


But anyway, I login, and get a white screen with a grey square in the middle, and I can't do anything from that point on - the keyboard/mouse no longer work. I have to restart kdm to get the login screen back (remotely via ssh).

---

