---
title: "Help!? Installing tar.gz"
date: 2008-11-19
forum: General Help
---

### Post by barnacles on 2008-11-19
I am attempting to install a vpn client for my university wifi. 

I have extracted the files successfully to the desktop to a folder named vpnclient. 

when i navigate to that folder in the terminal and attempt ./configure i get.. 

> dave@dave-laptop:~/Desktop/vpnclient$ ./configure
bash: ./configure: No such file or directory


I have installed the build essentials "sudo get-apt install build-essentials"

Help?

---

### Post by steveneddy on 2008-11-19
Follow this link from one of the links in my sig:

[http://www.psychocats.net/ubuntu/installingsoftware#lastresorts](http://www.psychocats.net/ubuntu/installingsoftware#lastresorts)

---

### Post by taurus on 2008-11-19
What's the output of this command from a terminal?

```
ls -la ~/Desktop/vpnclient
```
And by the way, the package is build-essential.

---

### Post by barnacles on 2008-11-20
> **taurus said:**
> What's the output of this command from a terminal?

```
ls -la ~/Desktop/vpnclient
```
And by the way, the package is build-essential.

yeah im sorry, just mistyped it. heres your output.

> dave@dave-laptop:~$ ls -la ~/Desktop/vpnclient
total 5600
drwxr-xr-x 3 dave dave    4096 2008-11-19 22:04 .
drwxr-xr-x 3 dave dave    4096 2008-11-19 21:38 ..
-rwxr-xr-x 1 dave dave 1239648 2005-11-22 03:43 cisco_cert_mgr
-rw-r--r-- 1 dave dave   15974 2005-11-22 03:43 Cniapi.h
-rw-r--r-- 1 dave dave    4505 2005-11-22 03:43 configure.h
-rwxr-xr-x 1 dave dave 2178328 2005-11-22 03:43 cvpnd
-rwxr-xr-x 1 dave dave    1823 2005-11-22 03:43 driver_build.sh
-rw-r--r-- 1 dave dave    6301 2005-11-22 03:43 frag.c
-rw-r--r-- 1 dave dave     227 2005-11-22 03:43 frag.h
-rw-r--r-- 1 dave dave    4514 2005-11-22 03:43 GenDefs.h
-rw-r--r-- 1 dave dave   22011 2005-11-22 03:43 interceptor.c
-rw-r--r-- 1 dave dave    2524 2005-11-22 03:43 IPSecDrvOSFunctions.h
-rw-r--r-- 1 dave dave    5138 2005-11-22 03:43 IPSecDrvOS_linux.c
-rw-r--r-- 1 dave dave    1249 2005-11-22 03:43 IPSecDrvOS_linux.h
-rwxr-xr-x 1 dave dave  226668 2005-11-22 03:43 ipseclog
-rwxr-xr-x 1 dave dave  427248 2005-11-22 03:43 libdriver64.so
-rwxr-xr-x 1 dave dave  359476 2005-11-22 03:43 libdriver.so
-rwxr-xr-x 1 dave dave  361457 2005-11-22 03:43 libvpnapi.so
-rw-r--r-- 1 dave dave    4449 2005-11-22 03:43 license.rtf
-rw-r--r-- 1 dave dave    4130 2005-11-22 03:43 license.txt
-rw-r--r-- 1 dave dave   16993 2005-11-22 03:43 linuxcniapi.c
-rw-r--r-- 1 dave dave    1322 2005-11-22 03:43 linuxcniapi.h
-rw-r--r-- 1 dave dave       0 2008-11-19 22:04 .linuxcniapi.o.d
-rw-r--r-- 1 dave dave    1015 2005-11-22 03:43 linuxkernelapi.c
-rw-r--r-- 1 dave dave    1852 2005-11-22 03:43 linux_os.h
-rw-r--r-- 1 dave dave    1076 2005-11-22 03:43 Makefile
-rw-r--r-- 1 dave dave    1926 2005-11-22 03:43 mtu.h
-rwxr-xr-x 1 dave dave     707 2006-05-04 12:10 niu_offcampus.pcf
-rwxr-xr-x 1 dave dave     711 2006-05-04 12:10 niu_openline.pcf
drwxr-xr-x 2 dave dave    4096 2008-11-19 21:42 .tmp_versions
-rw-r--r-- 1 dave dave     859 2005-11-22 03:43 unixcniapi.h
-rw-r--r-- 1 dave dave     698 2005-11-22 03:43 unixkernelapi.h
-rw-r--r-- 1 dave dave   20265 2005-11-22 03:43 vpnapi.h
-rwxr-xr-x 1 dave dave  666260 2005-11-22 03:43 vpnclient
-rw-r--r-- 1 dave dave     172 2005-11-22 03:43 vpnclient.ini
-rwxr-xr-x 1 dave dave    2961 2005-11-22 03:43 vpnclient_init
-rwxr-xr-x 1 dave dave   13826 2005-11-22 03:43 vpn_install
-rw-r--r-- 1 dave dave    1008 2005-11-22 03:43 vpn_ioctl_linux.h
-rwxr-xr-x 1 dave dave    5992 2005-11-22 03:43 vpn_uninstall


---

### Post by taurus on 2008-11-20
Looks like there is nothing to config.  You can install it by running the vpn_install

```
sudo ./vpn_install
```
or 
```
make
```
and probably 
```
sudo make install
```
to install it.

---

### Post by barnacles on 2008-11-20
it works. however i am gettin an error upon installation. any ideas?

> dave@dave-laptop:~/Desktop/vpnclient$ sudo ./vpn_install
Cisco Systems VPN Client Version 4.8.00 (0490) Linux Installer
Copyright (C) 1998-2005 Cisco Systems, Inc. All Rights Reserved.

By installing this product you agree that you have read the
license.txt file (The VPN Client license) and will comply with
its terms. 


Directory where binaries will be installed [/usr/local/bin]

Automatically start the VPN service at boot time [yes]no

In order to build the VPN kernel module, you must have the
kernel headers for the version of the kernel you are running.


Directory containing linux kernel source code [/lib/modules/2.6.24-21-generic/build]

* Binaries will be installed in "/usr/local/bin".
* Modules will be installed in "/lib/modules/2.6.24-21-generic/CiscoVPN".
* The VPN service will *NOT* be started automatically at boot time.
* Kernel source from "/lib/modules/2.6.24-21-generic/build" will be used to build the module.

Is the above correct [y]y

Making module
make -C /lib/modules/2.6.24-21-generic/build SUBDIRS=/home/dave/Desktop/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-21-generic'
  CC [M]  /home/dave/Desktop/vpnclient/linuxcniapi.o
/home/dave/Desktop/vpnclient/linuxcniapi.c:12:26: error: linux/config.h: No such file or directory
In file included from /home/dave/Desktop/vpnclient/Cniapi.h:15,
                 from /home/dave/Desktop/vpnclient/linuxcniapi.c:27:
/home/dave/Desktop/vpnclient/GenDefs.h:113: error: conflicting types for &#8216;uintptr_t&#8217;
include/linux/types.h:40: error: previous declaration of &#8216;uintptr_t&#8217; was here
/home/dave/Desktop/vpnclient/linuxcniapi.c: In function &#8216;CniInjectReceive&#8217;:
/home/dave/Desktop/vpnclient/linuxcniapi.c:297: error: implicit declaration of function &#8216;skb_set_timestamp&#8217;
/home/dave/Desktop/vpnclient/linuxcniapi.c:331: error: &#8216;struct sk_buff&#8217; has no member named &#8216;nh&#8217;
/home/dave/Desktop/vpnclient/linuxcniapi.c:332: error: &#8216;struct sk_buff&#8217; has no member named &#8216;mac&#8217;
/home/dave/Desktop/vpnclient/linuxcniapi.c: In function &#8216;CniInjectSend&#8217;:
/home/dave/Desktop/vpnclient/linuxcniapi.c:454: error: &#8216;struct sk_buff&#8217; has no member named &#8216;mac&#8217;
/home/dave/Desktop/vpnclient/linuxcniapi.c:455: error: &#8216;struct sk_buff&#8217; has no member named &#8216;nh&#8217;
/home/dave/Desktop/vpnclient/linuxcniapi.c:458: error: &#8216;struct sk_buff&#8217; has no member named &#8216;h&#8217;
/home/dave/Desktop/vpnclient/linuxcniapi.c:458: error: &#8216;struct sk_buff&#8217; has no member named &#8216;nh&#8217;
make[2]: *** [/home/dave/Desktop/vpnclient/linuxcniapi.o] Error 1
make[1]: *** [_module_/home/dave/Desktop/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-21-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".


---

### Post by barnacles on 2008-11-20
to the top, anyone?

---

### Post by barnacles on 2008-11-26
bump. still haven't figured it out. ANYBODY?

---

