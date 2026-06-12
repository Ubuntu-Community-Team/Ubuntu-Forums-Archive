---
title: "Natty 11.04 fresh install on Inspiron 8100 - no graphics"
date: 2011-06-02
forum: Hardware
---

### Post by danielsender on 2011-06-02
Hi,

I just did a fresh install of 11.04 on an Inspiron 8100 (not an upgrade). This machine has the Nvidia GeForce2Go graphic subsystem. When it had Maverick 10.10 it was working fine. However now, does not go beyond a few transactions that are shown in the console. It does not go into graphic mode. Below are the messages that appear when I typed "startx". I will appreciate any help.

Daniel

```

X.Org X Server 1.10.1
Release Date: 2011-04-15
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
Current Operating System: Linux agnes 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=c73ec0ed-a3d7-40c1-a24c-cb824170c69d ro quiet splash vt.handoff=7
Build Date: 21 May 2011  11:38:35AM
xorg-server 2:1.10.1-1ubuntu1.1 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.20.2
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Jun  2 11:38:45 2011
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(EE) Failed to load module "nvidia" (module does not exist, 0)
(EE) Failed to load module "nv" (module does not exist, 0)
(EE) NOUVEAU(0): Error allocating scanout buffer: 0

Fatal server error:
AddScreen/ScreenInit failed for driver 0


Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log
xinit: giving up
xinit: unable to connect to X server: Connection refused
xinit: server error

```

---

