---
title: "Installation Errors Every Time"
date: 2009-02-07
forum: Installation &amp; Upgrades
---

### Post by benf101 on 2009-02-07
I seem to always have the same problem whenever I need to install anything outside of the package installer method.  I am currently trying to get Cisco VPN installed and it falls apart at the same place every time.  I've tried hacking at it with different uneducated guesses but to no avail.  Here's what I'm doing:

[FONT="Courier New"]benjamin@GENIUS:/home/vpnclient$ sudo ./vpn_install
Cisco Systems VPN Client Version 4.8.00 (0490) Linux Installer
Copyright (C) 1998-2005 Cisco Systems, Inc. All Rights Reserved.

By installing this product you agree that you have read the
license.txt file (The VPN Client license) and will comply with
its terms. 


Directory where binaries will be installed [/usr/local/bin]

Automatically start the VPN service at boot time [yes]

In order to build the VPN kernel module, you must have the
kernel headers for the version of the kernel you are running.


Directory containing linux kernel source code [/lib/modules/2.6.24-19-generic/build]

* Binaries will be installed in "/usr/local/bin".
* Modules will be installed in "/lib/modules/2.6.24-19-generic/CiscoVPN".
* The VPN service will be started AUTOMATICALLY at boot time.
* Kernel source from "/lib/modules/2.6.24-19-generic/build" will be used to build the module.

Is the above correct [y]

Making module
make -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/home/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /home/vpnclient/linuxcniapi.o
In file included from /home/vpnclient/Cniapi.h:15,
                 from /home/vpnclient/linuxcniapi.c:30:
/home/vpnclient/GenDefs.h:113: error: conflicting types for &#8216;uintptr_t&#8217;
include/linux/types.h:40: error: previous declaration of &#8216;uintptr_t&#8217; was here
make[2]: *** [/home/vpnclient/linuxcniapi.o] Error 1
make[1]: *** [_module_/home/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".
benjamin@GENIUS:/home/vpnclient$ [/FONT]

Help is appreciated!  Thanks to all...

---

### Post by Pumalite on 2009-02-07
[http://www.lamnk.com/blog/domain/how-to-install-cisco-vpn-client-on-ubuntu-hardy-heron-804/](http://www.lamnk.com/blog/domain/how-to-install-cisco-vpn-client-on-ubuntu-hardy-heron-804/)

---

### Post by benf101 on 2009-02-07
Well, it looked promising, but nothing new.  After following those steps I got the same stuff:

[FONT="Courier New"][SIZE="2"]
benjamin@GENIUS:/home/vpnclient$ patch < ./vpnclient-linux-2.6.24-final.diff
bash: ./vpnclient-linux-2.6.24-final.diff: No such file or directory
benjamin@GENIUS:/home/vpnclient$ sudo ./vpn_install
Cisco Systems VPN Client Version 4.8.00 (0490) Linux Installer
Copyright (C) 1998-2005 Cisco Systems, Inc. All Rights Reserved.

By installing this product you agree that you have read the
license.txt file (The VPN Client license) and will comply with
its terms. 


Directory where binaries will be installed [/usr/local/bin]

Automatically start the VPN service at boot time [yes]

In order to build the VPN kernel module, you must have the
kernel headers for the version of the kernel you are running.


Directory containing linux kernel source code [/lib/modules/2.6.24-19-generic/build]

* Binaries will be installed in "/usr/local/bin".
* Modules will be installed in "/lib/modules/2.6.24-19-generic/CiscoVPN".
* The VPN service will be started AUTOMATICALLY at boot time.
* Kernel source from "/lib/modules/2.6.24-19-generic/build" will be used to build the module.

Is the above correct [y]

Making module
make -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/home/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /home/vpnclient/linuxcniapi.o
In file included from /home/vpnclient/Cniapi.h:15,
                 from /home/vpnclient/linuxcniapi.c:30:
/home/vpnclient/GenDefs.h:113: error: conflicting types for ‘uintptr_t’
include/linux/types.h:40: error: previous declaration of ‘uintptr_t’ was here
make[2]: *** [/home/vpnclient/linuxcniapi.o] Error 1
make[1]: *** [_module_/home/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".
benjamin@GENIUS:/home/vpnclient$ [/SIZE][/FONT]


[FONT="Arial"]BUT, the good news is that I uninstalled vpnc through Synaptic and then reinstalled and now KVPNC works... almost.  I'm getting a "Host could not be resolved" error, but I think that's a sign that MY end is properly installed and I can blame the host... right?[/FONT]

---

### Post by Pumalite on 2009-02-07
[http://ubuntuforums.org/showthread.php?t=743832](http://ubuntuforums.org/showthread.php?t=743832)

---

### Post by benf101 on 2009-02-07
That was helpful.  It now says I'm connected, however I do not have any special "inside" access.  It's like I'm not connected at all, and yet there are no errors.  Now I don't know where to debug... er, ask someone else on the forum to debug.  ;)

---

### Post by benf101 on 2009-02-07
Here's what I see, just so you know:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=102558&d=1234041517[/IMG]

---

### Post by Pumalite on 2009-02-07
Are you behind a proxy?

---

### Post by avtolle on 2009-02-07
I'm no expert, but I suggest taking a look at post #4 of the linked thread again. Somehow, I've a feeling this may be your answer.

---

