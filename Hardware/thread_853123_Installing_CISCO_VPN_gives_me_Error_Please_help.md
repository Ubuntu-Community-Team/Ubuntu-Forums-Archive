---
title: "Installing CISCO VPN gives me Error::: Please help"
date: 2008-07-08
forum: Hardware
---

### Post by psylvester on 2008-07-08
root@framedrelay-laptop:/etc/vpnc# 
root@framedrelay-laptop:/etc/vpnc# cd /home/framedrelay/Desktop/
root@framedrelay-laptop:/home/framedrelay/Desktop# ls
UGent.pcf  vpnclient-linux-x86_64-4.8.00.0490-k9.tar.gz
root@framedrelay-laptop:/home/framedrelay/Desktop# 
root@framedrelay-laptop:/home/framedrelay/Desktop# 
root@framedrelay-laptop:/home/framedrelay/Desktop# tar -xvf vpnclient-linux-x86_64-4.8.00.0490-k9.tar.gz 
vpnclient/
vpnclient/libvpnapi.so
vpnclient/vpnapi.h
vpnclient/cisco_cert_mgr
vpnclient/vpnclient
vpnclient/ipseclog
vpnclient/cvpnd
vpnclient/vpn_install
vpnclient/vpnclient_init
vpnclient/vpn_uninstall
vpnclient/driver_build.sh
vpnclient/sample.pcf
vpnclient/vpnclient.ini
vpnclient/license.txt
vpnclient/license.rtf
vpnclient/interceptor.c
vpnclient/linuxcniapi.c
vpnclient/linuxcniapi.h
vpnclient/vpn_ioctl_linux.h
vpnclient/IPSecDrvOS_linux.c
vpnclient/linux_os.h
vpnclient/frag.h
vpnclient/frag.c
vpnclient/linuxkernelapi.c
vpnclient/GenDefs.h
vpnclient/mtu.h
vpnclient/IPSecDrvOSFunctions.h
vpnclient/IPSecDrvOS_linux.h
vpnclient/Cniapi.h
vpnclient/unixcniapi.h
vpnclient/unixkernelapi.h
vpnclient/config.h
vpnclient/libdriver64.so
vpnclient/libdriver.so
vpnclient/Makefile
root@framedrelay-laptop:/home/framedrelay/Desktop# ls
UGent.pcf  vpnclient  vpnclient-linux-x86_64-4.8.00.0490-k9.tar.gz
root@framedrelay-laptop:/home/framedrelay/Desktop# 
root@framedrelay-laptop:/home/framedrelay/Desktop# 
root@framedrelay-laptop:/home/framedrelay/Desktop# 

root@framedrelay-laptop:/home/framedrelay/Desktop# mv vpnclient /usr/local/
root@framedrelay-laptop:/home/framedrelay/Desktop# cd /usr/local/
root@framedrelay-laptop:/usr/local# cd vpnclient/
root@framedrelay-laptop:/usr/local/vpnclient# ls
cisco_cert_mgr  driver_build.sh  interceptor.c          ipseclog        license.rtf    linuxkernelapi.c  sample.pcf       vpnclient       vpn_ioctl_linux.h
Cniapi.h        frag.c           IPSecDrvOSFunctions.h  libdriver64.so  license.txt    linux_os.h        unixcniapi.h     vpnclient.ini   vpn_uninstall
config.h        frag.h           IPSecDrvOS_linux.c     libdriver.so    linuxcniapi.c  Makefile          unixkernelapi.h  vpnclient_init
cvpnd           GenDefs.h        IPSecDrvOS_linux.h     libvpnapi.so    linuxcniapi.h  mtu.h             vpnapi.h         vpn_install
root@framedrelay-laptop:/usr/local/vpnclient# 
root@framedrelay-laptop:/usr/local/vpnclient# 
root@framedrelay-laptop:/usr/local/vpnclient# uname -r
2.6.24-19-generic


root@framedrelay-laptop:/usr/local/vpnclient# sudo apt-get install linux-headers-`uname -r`
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.24-19-generic is already the newest version.
linux-headers-2.6.24-19-generic set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

[COLOR="Red"]
root@framedrelay-laptop:/usr/local/vpnclient# make
make -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/usr/local/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /usr/local/vpnclient/linuxcniapi.o
/usr/local/vpnclient/linuxcniapi.c:12:26: error: linux/config.h: No such file or directory
In file included from /usr/local/vpnclient/Cniapi.h:15,
                 from /usr/local/vpnclient/linuxcniapi.c:27:
/usr/local/vpnclient/GenDefs.h:113: error: conflicting types for ‘uintptr_t’
include/linux/types.h:40: error: previous declaration of ‘uintptr_t’ was here
/usr/local/vpnclient/linuxcniapi.c: In function ‘CniInjectReceive’:
/usr/local/vpnclient/linuxcniapi.c:297: error: implicit declaration of function ‘skb_set_timestamp’
/usr/local/vpnclient/linuxcniapi.c:331: error: ‘struct sk_buff’ has no member named ‘nh’
/usr/local/vpnclient/linuxcniapi.c:332: error: ‘struct sk_buff’ has no member named ‘mac’
/usr/local/vpnclient/linuxcniapi.c: In function ‘CniInjectSend’:
/usr/local/vpnclient/linuxcniapi.c:454: error: ‘struct sk_buff’ has no member named ‘mac’
/usr/local/vpnclient/linuxcniapi.c:455: error: ‘struct sk_buff’ has no member named ‘nh’
/usr/local/vpnclient/linuxcniapi.c:458: error: ‘struct sk_buff’ has no member named ‘h’
/usr/local/vpnclient/linuxcniapi.c:458: error: ‘struct sk_buff’ has no member named ‘nh’
make[2]: *** [/usr/local/vpnclient/linuxcniapi.o] Error 1
make[1]: *** [_module_/usr/local/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [default] Error 2

[/COLOR]



root@framedrelay-laptop:/usr/local/vpnclient# sudo ./vpn_install 
[COLOR="Red"]Cisco Systems VPN Client Version 4.8.00 (0490) Linux Installer
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

Is the above correct [y]y

Making module
make -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/usr/local/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /usr/local/vpnclient/linuxcniapi.o
/usr/local/vpnclient/linuxcniapi.c:12:26: error: linux/config.h: No such file or directory
In file included from /usr/local/vpnclient/Cniapi.h:15,
                 from /usr/local/vpnclient/linuxcniapi.c:27:
/usr/local/vpnclient/GenDefs.h:113: error: conflicting types for ‘uintptr_t’
include/linux/types.h:40: error: previous declaration of ‘uintptr_t’ was here
/usr/local/vpnclient/linuxcniapi.c: In function ‘CniInjectReceive’:
/usr/local/vpnclient/linuxcniapi.c:297: error: implicit declaration of function ‘skb_set_timestamp’
/usr/local/vpnclient/linuxcniapi.c:331: error: ‘struct sk_buff’ has no member named ‘nh’
/usr/local/vpnclient/linuxcniapi.c:332: error: ‘struct sk_buff’ has no member named ‘mac’
/usr/local/vpnclient/linuxcniapi.c: In function ‘CniInjectSend’:
/usr/local/vpnclient/linuxcniapi.c:454: error: ‘struct sk_buff’ has no member named ‘mac’
/usr/local/vpnclient/linuxcniapi.c:455: error: ‘struct sk_buff’ has no member named ‘nh’
/usr/local/vpnclient/linuxcniapi.c:458: error: ‘struct sk_buff’ has no member named ‘h’
/usr/local/vpnclient/linuxcniapi.c:458: error: ‘struct sk_buff’ has no member named ‘nh’
make[2]: *** [/usr/local/vpnclient/linuxcniapi.o] Error 1
make[1]: *** [_module_/usr/local/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".
root@framedrelay-laptop:/usr/local/vpnclient# [/COLOR]


please someone help. CISCO VPN is much needed .. :(

---

### Post by psylvester on 2008-07-08
I browsed few threads, one was kind of similar - which suggests to install a patch, tried that as well.



root@framedrelay-laptop:/usr/local/vpnclient# 
root@framedrelay-laptop:/usr/local/vpnclient#  wget -q [http://projects.tuxx-home.at/ciscovpn/patches/vpnclient-linux-2.6.24-final.diff](http://projects.tuxx-home.at/ciscovpn/patches/vpnclient-linux-2.6.24-final.diff)
 
root@framedrelay-laptop:/usr/local/vpnclient# 

root@framedrelay-laptop:/usr/local/vpnclient# sudo apt-get install patch
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  diff-doc
The following NEW packages will be installed:
  patch
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 95.6kB of archives.
After this operation, 193kB of additional disk space will be used.
Get:1 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/main patch 2.5.9-4 [95.6kB]
Fetched 95.6kB in 0s (114kB/s)
Selecting previously deselected package patch.
(Reading database ... 131252 files and directories currently installed.)
Unpacking patch (from .../patch_2.5.9-4_i386.deb) ...
Setting up patch (2.5.9-4) ...
root@framedrelay-laptop:/usr/local/vpnclient# patch vpnclient-linux-2.6.24-final.diff

root@framedrelay-laptop:/usr/local/vpnclient# patch < vpnclient-linux-2.6.24-final.diff
patching file GenDefs.h
patching file interceptor.c
Hunk #1 succeeded at 24 (offset -4 lines).
Hunk #2 succeeded at 48 (offset -4 lines).
[COLOR="Red"]Hunk #3 FAILED at 107.
Hunk #4 succeeded at 123 (offset -23 lines).
Hunk #5 FAILED at 350.
Hunk #6 succeeded at 849 (offset -86 lines).
Hunk #7 succeeded at 891 (offset -86 lines).
2 out of 7 hunks FAILED -- saving rejects to file interceptor.c.rej[/COLOR]

root@framedrelay-laptop:/usr/local/vpnclient# 
root@framedrelay-laptop:/usr/local/vpnclient# 

[COLOR="Red"]root@framedrelay-laptop:/usr/local/vpnclient# **sudo ./vpn_install **
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

Is the above correct [y]y

Making module
make -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/usr/local/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /usr/local/vpnclient/linuxcniapi.o
/usr/local/vpnclient/linuxcniapi.c:12:26: error: linux/config.h: No such file or directory
/usr/local/vpnclient/linuxcniapi.c: In function ‘CniInjectReceive’:
/usr/local/vpnclient/linuxcniapi.c:297: error: implicit declaration of function ‘skb_set_timestamp’
/usr/local/vpnclient/linuxcniapi.c:331: error: ‘struct sk_buff’ has no member named ‘nh’
/usr/local/vpnclient/linuxcniapi.c:332: error: ‘struct sk_buff’ has no member named ‘mac’
/usr/local/vpnclient/linuxcniapi.c: In function ‘CniInjectSend’:
/usr/local/vpnclient/linuxcniapi.c:454: error: ‘struct sk_buff’ has no member named ‘mac’
/usr/local/vpnclient/linuxcniapi.c:455: error: ‘struct sk_buff’ has no member named ‘nh’
/usr/local/vpnclient/linuxcniapi.c:458: error: ‘struct sk_buff’ has no member named ‘h’
/usr/local/vpnclient/linuxcniapi.c:458: error: ‘struct sk_buff’ has no member named ‘nh’
make[2]: *** [/usr/local/vpnclient/linuxcniapi.o] Error 1
make[1]: *** [_module_/usr/local/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".[/COLOR]

---

### Post by Fire_Chief on 2008-07-08
The Cisco VPN client for Linux you currently have is over two years old (4.8.00.0490). Try using the latest version (4.8.02.0030). I just downloaded it and ran the install script (as root). It compiled and installed properly. Was also able to connect to a remote network on the first try. I am running 8.04 with the gvpndialer gui (great front end for Cisco VPN client).

Cheers!

---

### Post by psylvester on 2008-07-10
I dont think your answered helped me in anyway.
I still get the same error.
Im afraid whether the path that I'm giving is correct.

Directory containing linux kernel source code [/lib/modules/2.6.24-19-generic/build]

because its complaining abt some header files missing?

Please ! someone help me.

---

### Post by Fire_Chief on 2008-07-10
Do you see any files in the designated path for the kernel source (/lib/modules/2.6.24-19-generic/build)? If not, then you may need to install the kernel source package (not the same as the headers).

Try ```
sudo apt-get install linux-generic
```
This will download the latest kernel source for your kernel version. Then try running the vpn_install script again.

Cheers!

---

### Post by timcredible on 2008-07-10
definitely get the latest vpn client.  in the readme of the newest client, it says that one of the fixes is that the older client didn't install with kernel 2.6.19+, and ubuntu uses:

tim@vostro:~$ uname -r
2.6.24-16-generic

also, if there's header files missing, install them via synaptic - just install everything that has linux-header-2.6.24-16 in the name.

---

### Post by Fire_Chief on 2008-07-28
Hi psylvester,

Did you have any success with the newer version of the Cisco VPN client?

Cheers!

---

