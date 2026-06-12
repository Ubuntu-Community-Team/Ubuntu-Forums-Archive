---
title: "Ubuntu 9.04 randomly not starting xorg."
date: 2009-06-08
forum: Installation &amp; Upgrades
---

### Post by qedqed on 2009-06-08
Hello,

i decided to switch from my Debian squeeze to **Ubuntu 9.04 amd64** even on my desktop (_Intel Core duo, GeForce 8800 GTX_).

[LIST]
[*]Created the Boot device, installed with no particular configuration... just Language and KB.

[*]Reboot

[*]GDM was not starting, reboot GDM not starting, reboot GDM starting and  everything working.
[/LIST]

The day after all over again. I even apt-get dist-upgrade but nothing changed.

After extended test, i have 1/3 chance to start a workig xorg. Everything with the default installation.
After updating packets and installing nvidia.com drivers nothing changed at all.
This system was working flawless with Debian/Windows XP.


That's what i got when startx isnt working


```
X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-15-server x86_64 Ubuntu
Current Operating System: Linux qed-desktop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 x86_64
Build Date: 09 April 2009  02:11:54AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@crested.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Jun  8 02:45:00 2009
(==) Using config file: "/etc/X11/xorg.conf"


Backtrace:
0: /usr/bin/X11/X(xorg_backtrace+0x26) [0x4f1b66]
1: /usr/bin/X11/X(xf86SigHandler+0x41) [0x485a61]
2: /lib/libc.so.6 [0x7fcabd8e0040]
3: /usr/lib/libpciaccess.so.0(pci_device_get_bridge_buses+0x91) [0x7fcabf98c091]
4: /usr/bin/X11/X(initPciBusState+0x8d) [0x49ec4d]
5: /usr/bin/X11/X(xf86AccessInit+0xe) [0x47d6fe]
6: /usr/bin/X11/X(InitOutput+0xef8) [0x46fad8]
7: /usr/bin/X11/X(main+0x20e) [0x433bde]
8: /lib/libc.so.6(__libc_start_main+0xe6) [0x7fcabd8cb5a6]
9: /usr/bin/X11/X [0x433219]
Saw signal 11.  Server aborting.
 ddxSigGiveUp: Closing log
 ddxSigGiveUp: re-raising 11
giving up.
xinit:  Connection refused (errno 111):  unable to connect to X server
xinit:  No such process (errno 3):  Server error.

```


I tried everything, i rly dont have a clue about what to do.

---

