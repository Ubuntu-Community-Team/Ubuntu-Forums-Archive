---
title: "Installing driver 8800gts"
date: 2009-03-12
forum: Installation &amp; Upgrades
---

### Post by br41ns70rm on 2009-03-12
Hey,

I am new here to the forum and quite new to linux.
but i am trying to install my nvidia driver for my 2x xfx 8800gts video cards and of course this fails.

i'd even tried some solved forum threads but still nothing (maybe becouse i dont understand linux that well), i get stuck after de usplash in a terminal liked screen where i can log in.

i get this message:
> Boot from (hd0,5) ext3   22756627-1ac7-4c20-9188-4a976ca5609f
starting up ...
Londing, please wati...
19+0 records in
19+0 records out
kinit: name_to_dev_t(/dev/disk/by-uuid/cb71dade-7033-4946-9755-8ed0ab262804) = dev(8,21)
kinit: trying to resume from /dev/disk/by-uuid/cb71dade-7033-4946-9755-8ed0ab262804
kinit: No resume image, doing normal boot...

ubuntu 8.10 Brx tty1

Brx login:

if there is somebody who can help me trough this step by step i would realy be gratefull.

---

### Post by br41ns70rm on 2009-03-13
If i try startx i get this message:

> X.Org X server 1.5.2
Release Date 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux Brx 2.6.27-7-generic #1 SMP Fri Oct 24 06:42:44 UTC 2008 i686
Build Date: 24 October 2008  08:00:16AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@rothera.buildd)
Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
to make sure that you have the latest version.
Module Loader present
Markers: (--)probed, (**) from config file, (==) default settings, (++) from command line, (!!) notice, (II) informational, (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Mar 13 12:56:06 2009
(==) Using config file: "/etc/X11/xorg.conf"
Primary device is not PCI
(EE) No devices detected

Fatal server error:
no screens found
giving up.
xinit: Connection refused (errno 111): unable to connect to X server
xinit: No such process (errno 3): Server error.

---

