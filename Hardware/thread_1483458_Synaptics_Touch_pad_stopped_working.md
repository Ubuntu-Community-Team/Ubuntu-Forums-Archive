---
title: "Synaptics Touch pad stopped working"
date: 2010-05-14
forum: Hardware
---

### Post by nmyrick on 2010-05-14
I have an Acer 4720Z laptop, and my touchpad has stopped working after I used Fn+F7 to disable it, then turned off the laptop.

Fn+F7 had worked previously to enable and disable the touchpad.  Now, after I disabled the touchpad and rebooted, the touchpad does not work, and the Fn+F7 key combination does not help. 

I tried reinstalling 'xserver-xorg-input-synaptics'(Synaptics touchpad driver for X.Org server), and then restarting, but that did not help either.

This also happened after I installed Podslueth for Banshee, since Banshee was not detecting my second gen IPod nano, but I don't think that would have affected the touchpad.

Here is the log for an XOrg update that I must have installed this morning, along with other updates.  This is about the same time that I started having this problem.

[COLOR="Navy"]X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-25-server i686 Ubuntu
Current Operating System: Linux laptop1 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-22-generic root=UUID=338f9d8b-183e-4fed-8c09-c158d50efb65 ro quiet splash
Build Date: 23 April 2010  05:11:50PM
xorg-server 2:1.7.6-2ubuntu7 (Bryce Harrington <bryce@ubuntu.com>) 
Current version of pixman: 0.16.4
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.1.log", Time: Fri May 14 10:54:37 2010
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) No Layout section.  Using the first Screen section.
(==) No screen section available. Using defaults.
(**) |-->Screen "Default Screen Section" (0)
(**) |   |-->Monitor "<default monitor>"
(==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
(II) Loader magic: 0x81f0e80
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 6.0
	X.Org XInput driver : 7.0
	X.Org Server Extension : 2.0
(--) using VT number 8

(--) PCI:*(0:0:2:0) 8086:2a02:1025:011d Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller rev 3, Mem @ 0xf0000000/1048576, 0xd0000000/268435456, I/O @ 0x00001800/8
(--) PCI: (0:0:2:1) 8086:2a03:1025:011d Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller rev 3, Mem @ 0xf0100000/1048576
(II) Open ACPI successful (/var/run/acpid.socket)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0[/COLOR]

I noticed that the log time is Friday, May 14th at 10:54, which is about the same time the issue started.  I also noticed the Linux kernel version changed from a previous log which showed 2.6.32-21, to the one in this log which is 2.6.32-22.


I am at a loss here. Can someone help?

I have Ubuntu 10.04, and the Synaptics touchpad has been working up until now.

---

