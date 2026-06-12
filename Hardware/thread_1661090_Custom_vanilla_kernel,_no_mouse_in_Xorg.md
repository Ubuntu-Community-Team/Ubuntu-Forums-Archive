---
title: "Custom vanilla kernel, no mouse in Xorg"
date: 2011-01-06
forum: Hardware
---

### Post by executivul on 2011-01-06
Hello all,
I'm building a custom vanilla kernel + simple initramfs which boots a minimal ubuntu maverick distro (command line install + xorg).

Booting the default Ubuntu kernel everything is ok.
With my kernel Xorg starts but the mouse is frozen in the middle of the screen. Console mouse via gpm works ok though.

Xorg has no configuration file, I guess it detects devices at runtime.

Please help. If I posted in the wrong forum please move to the correct one.

---

### Post by executivul on 2011-01-06
Adding:

Section "ServerFlags"
    Option "AutoAddDevices" "Off"
EndSection

solved the mouse problem, but the keyboard does not work now:

root@CLIENT:~# startx


X.Org X Server 1.9.0
Release Date: 2010-08-20
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
Current Operating System: Linux CLIENT 2.6.36-mss1 #227 SMP Thu Jan 6 16:14:25 EET 2011 i686
Kernel command line: vga=791 splash=verbose INIT_VERBOSE=yes  BOOT_IMAGE=bzImage ip=10.0.0.31:10.0.0.1:10.0.0.1:255.255.255.0 
Build Date: 16 September 2010  05:39:22PM
xorg-server 2:1.9.0-0ubuntu7 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.18.4
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Jan  6 17:38:32 2011
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(EE) Failed to load module "kbd" (module does not exist, 0)
(EE) Failed to load module "kbd" (module does not exist, 0)
(EE) No input driver matching `kbd'
^C

---

### Post by executivul on 2011-01-07
It seems that by selecting no AutoAddDevices, xorg fallsback to "manual" driver selection, but after Lucid the "kbd" driver is included no more, that's why I have mouse but no keyboard.

How to debug udev?
Why udevadm reports both mouse and keyboard but xorg picks none?
Is it a kernel config issue, a kernel version uncompatibility or something missing from my initrd scripts?

---

