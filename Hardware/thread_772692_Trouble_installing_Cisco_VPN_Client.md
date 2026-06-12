---
title: "Trouble installing Cisco VPN Client"
date: 2008-04-28
forum: Hardware
---

### Post by griehl2490 on 2008-04-28
I need to have the Cisco Systems VPN Client on my computer to be able to connect to the wireless internet when I'm on campus at school. I downloaded the linux tar.gz version of it from our ITS website and extracted it to my desktop and the documentation says to just do
```
cd /vpnclient
sudo ./vpn_install
```
Which is what I do and then I type in my password and what not and this is what my terminal says afterwards.
```
greg@greg-laptop:~$ cd /home/greg/Desktop/vpnclient
greg@greg-laptop:~/Desktop/vpnclient$ sudo ./vpn_install
[sudo] password for greg: 
Cisco Systems VPN Client Version 4.8.01 (0640) Linux Installer
Copyright (C) 1998-2006 Cisco Systems, Inc. All Rights Reserved.

By installing this product you agree that you have read the
license.txt file (The VPN Client license) and will comply with
its terms. 


Directory where binaries will be installed [/usr/local/bin]

Automatically start the VPN service at boot time [yes]

In order to build the VPN kernel module, you must have the
kernel headers for the version of the kernel you are running.


Directory containing linux kernel source code [/lib/modules/2.6.24-16-generic/build]

* Binaries will be installed in "/usr/local/bin".
* Modules will be installed in "/lib/modules/2.6.24-16-generic/CiscoVPN".
* The VPN service will be started AUTOMATICALLY at boot time.
* Kernel source from "/lib/modules/2.6.24-16-generic/build" will be used to build the module.

Is the above correct [y]

Making module
make -C /lib/modules/2.6.24-16-generic/build SUBDIRS=/home/greg/Desktop/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /home/greg/Desktop/vpnclient/linuxcniapi.o
In file included from /home/greg/Desktop/vpnclient/Cniapi.h:15,
                 from /home/greg/Desktop/vpnclient/linuxcniapi.c:31:
/home/greg/Desktop/vpnclient/GenDefs.h:113: error: conflicting types for &#8216;uintptr_t&#8217;
include/linux/types.h:40: error: previous declaration of &#8216;uintptr_t&#8217; was here
make[2]: *** [/home/greg/Desktop/vpnclient/linuxcniapi.o] Error 1
make[1]: *** [_module_/home/greg/Desktop/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".

```

---

### Post by NetworkGuy on 2008-04-28
Check out vpnc in the respositories.   It works great for me and maybe will for you also.   If you must use the Cisco client, it looks like you need to "sudo aptitude install build-essential" from the terminal.

---

### Post by griehl2490 on 2008-04-28
I'm not sure if they vpnc thing will work because the cisco vpn thing comes with all of the penn state internet connections set up in it and all i need is my username and password.

however, I tried the sudo aptitude install build-essential and afterwards did the sudo ./vpn_install and still does the same exact thing as above.

---

### Post by griehl2490 on 2008-04-28
I installed the vpnc and the network-manager-vpnc from synaptec but I can't really test if they work....nor can I find them in any of my menus up top.

---

### Post by Rinzwind on 2008-04-28
Linux 2.6.24 (which ships with Ubuntu 8.04) moved some headers and symbols around, and breaks VMWare... So I guess it also breaks your vpn cisco client. I found your problem here: [http://diamondsw.dyndns.org/Home/Et_Cetera/Entries/2008/4/25_Linux_2.6.24_and_VMWare.html](http://diamondsw.dyndns.org/Home/Et_Cetera/Entries/2008/4/25_Linux_2.6.24_and_VMWare.html)

It states how to fix your problem but it is related to VMWare and not this client.

Either you bug Cisco for a Ubuntu 8.04 client ;) or you follow that link and change anything related to VMWare for your Cisco client. Or back to an older kernel ;) Anyway you go... you are in a bit of a problem getting this working...

---

### Post by ndeburn on 2008-04-28
If you want to get Cisco working, follow my steps in:
[http://ubuntuforums.org/showthread.php?t=769273]("http://ubuntuforums.org/showthread.php?t=769273")

That will take care of it.

---

### Post by griehl2490 on 2008-04-28
> **NetworkGuy said:**
> Check out vpnc in the respositories.   It works great for me and maybe will for you also.   If you must use the Cisco client, it looks like you need to "sudo aptitude install build-essential" from the terminal.

How would I set up the vpnc to connect to the Penn State internet connection then? I'm not exactly sure where to go from there. I found it in my internet connection thigns at the top of the my screen.

---

### Post by xzsmhq on 2008-05-01
"How would I set up the vpnc to connect to the Penn State internet connection then?" Penn State uses a Proxy??? Sometimes if you have the proxy set on your local box before you VPN in you can't use the internet.... Uncheck your proxy settings before VPNing in.. Then remote to a computer and use that PC or yours....

---

### Post by altjx on 2010-10-13
Old thread but I'm getting this same error. 

```
alton@alton-desktop:~/Downloads/vpnclient$ sudo ./vpnclient_install
sudo: ./vpnclient_install: command not found
alton@alton-desktop:~/Downloads/vpnclient$ ls
cisco_cert_mgr   GenDefs.h              license.rtf    sample.pcf
cisco_ipsec      interceptor.c          license.txt    unixcniapi.h
Cniapi.h         interceptor.o          linuxcniapi.c  vpnclient
config.h         IPSecDrvOSFunctions.h  linuxcniapi.h  vpnclient.ini.in
cvpnd            IPSecDrvOS_linux.c     linuxcniapi.o  vpnclient_init
driver_build.sh  IPSecDrvOS_linux.h     linux_os.h     vpn_install
frag.c           IPSecDrvOS_linux.o     Makefile       vpn_ioctl_linux.h
frag.h           ipseclog               mtu.h          vpn_uninstall
frag.o           libdriver.so           profiles
alton@alton-desktop:~/Downloads/vpnclient$ sudo ./vpn_install 
Cisco Systems VPN Client Version 4.0.5 (Rel) Linux Installer
Copyright (C) 1998-2001 Cisco Systems, Inc. All Rights Reserved.

By installing this product you agree that you have read the
license.txt file (The VPN Client license) and will comply with
its terms. 


Directory where binaries will be installed [/usr/local/bin] 

Automatically start the VPN service at boot time [yes] 

In order to build the VPN kernel module, you must have the
kernel headers for the version of the kernel you are running.

For RedHat 6.x users these files are installed in /usr/src/linux by default
For RedHat 7.x users these files are installed in /usr/src/linux-2.4 by default
For Suse 7.3 users these files are installed in /usr/src/linux-2.4.10.SuSE by default

Directory containing linux kernel source code [/lib/modules/2.6.35-22-generic/build] 

* Binaries will be installed in "/usr/local/bin".
* Modules will be installed in "/lib/modules/2.6.35-22-generic/CiscoVPN".
* The VPN service will be started AUTOMATICALLY at boot time.
* Kernel source from "/lib/modules/2.6.35-22-generic/build" will be used to build the module.

Is the above correct [y] 

Making module
make -C /lib/modules/2.6.35-22-generic/build SUBDIRS=/home/alton/Downloads/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-22-generic'
  CC [M]  /home/alton/Downloads/vpnclient/linuxcniapi.o
/home/alton/Downloads/vpnclient/linuxcniapi.c:12: fatal error: linux/config.h: No such file or directory
compilation terminated.
make[2]: *** [/home/alton/Downloads/vpnclient/linuxcniapi.o] Error 1
make[1]: *** [_module_/home/alton/Downloads/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".

```

---

### Post by OpenThinking on 2010-11-24
I'm getting the same error (almost). I'm using Ubuntu 10.10.
I've read the following page and downloaded the source and patch from it:
[http://www.longren.org/2007/05/17/how-to-cisco-vpn-client-on-ubuntu-704-feisty-fawn/]("http://www.longren.org/2007/05/17/how-to-cisco-vpn-client-on-ubuntu-704-feisty-fawn/")

**Getting the following error:**

Making module
make -C /lib/modules/2.6.35-22-generic-pae/build SUBDIRS=/home/name/Hämtningar/vpnclient modules
make[1]: Går till katalogen "/usr/src/linux-headers-2.6.35-22-generic-pae"
  CC [M]  /home/name/Hämtningar/vpnclient/linuxcniapi.o
/home/holm/Hämtningar/vpnclient/linuxcniapi.c:15: fatal error: linux/autoconf.h: Filen eller katalogen finns inte
compilation terminated.
make[2]: *** [/home/name/Hämtningar/vpnclient/linuxcniapi.o] Fel 1
make[1]: *** [_module_/home/name/Hämtningar/vpnclient] Fel 2
make[1]: Lämnar katalogen "/usr/src/linux-headers-2.6.35-22-generic-pae"
make: *** [default] Fel 2
Failed to make module "cisco_ipsec.ko".

---

### Post by OpenThinking on 2010-11-24
I'm getting the same error (almost). I'm using Ubuntu 10.10.
I've read the following page and downloaded the source and patch from it:
[http://www.longren.org/2007/05/17/how-to-cisco-vpn-client-on-ubuntu-704-feisty-fawn/]("http://www.longren.org/2007/05/17/how-to-cisco-vpn-client-on-ubuntu-704-feisty-fawn/")

**Getting the following error:**

Making module
make -C /lib/modules/2.6.35-22-generic-pae/build SUBDIRS=/home/name/Hämtningar/vpnclient modules
make[1]: Går till katalogen "/usr/src/linux-headers-2.6.35-22-generic-pae"
  CC [M]  /home/name/Hämtningar/vpnclient/linuxcniapi.o
/home/holm/Hämtningar/vpnclient/linuxcniapi.c:15: fatal error: linux/autoconf.h: Filen eller katalogen finns inte
compilation terminated.
make[2]: *** [/home/name/Hämtningar/vpnclient/linuxcniapi.o] Fel 1
make[1]: *** [_module_/home/name/Hämtningar/vpnclient] Fel 2
make[1]: Lämnar katalogen "/usr/src/linux-headers-2.6.35-22-generic-pae"
make: *** [default] Fel 2
Failed to make module "cisco_ipsec.ko".

---

### Post by InFro on 2010-11-29
I'm using 10.10 Ubuntu x64, used vpnclient-linux-x86_64-4.8.02.0030-k9.tar.gz from [http://tuxx-home.at/archives/2009/05/12/T19_03_01/]("http://tuxx-home.at/archives/2009/05/12/T19_03_01/") (also many other versions, patches, etc.).
No luck :/

Always getting "
Making module
make -C /lib/modules/2.6.35-23-generic/build SUBDIRS=/home/infro/programs/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-23-generic'
  CC [M]  /home/infro/programs/vpnclient/linuxcniapi.o
/home/infro/programs/vpnclient/linuxcniapi.c:14: fatal error: linux/autoconf.h: No such file or directory
compilation terminated.
make[2]: *** [/home/infro/programs/vpnclient/linuxcniapi.o] Error 1
make[1]: *** [_module_/home/infro/programs/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-23-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".
"

Anyone?

Maybe I need to install some linux kernel source package or sth? Never was good at compiling...

---

### Post by neoragexxx on 2010-11-30
try

cd vpnclient/setup/directory/
wget [http://www.lamnk.com/download/fixes.patch](http://www.lamnk.com/download/fixes.patch)
patch < ./fixes.patch
sudo ./vpn_install

cheers

check [http://www.lamnk.com/blog/vpn/how-to-install-cisco-vpn-client-on-ubuntu-jaunty-jackalope-and-karmic-koala-64-bit/](http://www.lamnk.com/blog/vpn/how-to-install-cisco-vpn-client-on-ubuntu-jaunty-jackalope-and-karmic-koala-64-bit/) 
for more details

---

### Post by vangop on 2010-12-12
Why don't you try vpnc? I have 2 companies with cisco vpn and vpnc works great for them. 
Check out
[http://ubuntu-answers.blogspot.com/2010/12/cisco-vpn-with-vpnc.html]("http://ubuntu-answers.blogspot.com/2010/12/cisco-vpn-with-vpnc.html") for more info

---

### Post by Rebootkid on 2010-12-14
> **neoragexxx said:**
> try

cd vpnclient/setup/directory/
wget [http://www.lamnk.com/download/fixes.patch](http://www.lamnk.com/download/fixes.patch)
patch < ./fixes.patch
sudo ./vpn_install

cheers

check [http://www.lamnk.com/blog/vpn/how-to-install-cisco-vpn-client-on-ubuntu-jaunty-jackalope-and-karmic-koala-64-bit/](http://www.lamnk.com/blog/vpn/how-to-install-cisco-vpn-client-on-ubuntu-jaunty-jackalope-and-karmic-koala-64-bit/) 
for more details

Thanks so much. This worked for me.

---

### Post by Rebootkid on 2010-12-14
> **vangop said:**
> Why don't you try vpnc? I have 2 companies with cisco vpn and vpnc works great for them. 
Check out
[http://ubuntu-answers.blogspot.com/2010/12/cisco-vpn-with-vpnc.html]("http://ubuntu-answers.blogspot.com/2010/12/cisco-vpn-with-vpnc.html") for more info

For me, VPNC works fine with PIX, Router, and VPN3000 concentrators.

It does not work with ASA devices

---

### Post by storm_m2138 on 2011-01-31
> **neoragexxx said:**
> try

cd vpnclient/setup/directory/
wget [http://www.lamnk.com/download/fixes.patch](http://www.lamnk.com/download/fixes.patch)
patch < ./fixes.patch
sudo ./vpn_install

cheers

check [http://www.lamnk.com/blog/vpn/how-to-install-cisco-vpn-client-on-ubuntu-jaunty-jackalope-and-karmic-koala-64-bit/](http://www.lamnk.com/blog/vpn/how-to-install-cisco-vpn-client-on-ubuntu-jaunty-jackalope-and-karmic-koala-64-bit/) 
for more details

Sweet worked. Thank you!

---

### Post by lamnk on 2011-02-23
> **vangop said:**
> Why don't you try vpnc? I have 2 companies with cisco vpn and vpnc works great for them. 
Check out
[http://ubuntu-answers.blogspot.com/2010/12/cisco-vpn-with-vpnc.html]("http://ubuntu-answers.blogspot.com/2010/12/cisco-vpn-with-vpnc.html") for more info
vpnc is great (i'm using it right now) however it supports tunneling over UDP only. For someone who is behind NAT it's recommended to use TCP encapsulation.

> **Rebootkid said:**
> For me, VPNC works fine with PIX, Router, and VPN3000 concentrators.

It does not work with ASA devices
That's right, but the Cisco VPN Client is also compatible with 3000 concentrator only.

---

