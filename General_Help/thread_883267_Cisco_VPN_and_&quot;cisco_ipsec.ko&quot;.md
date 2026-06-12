---
title: "Cisco VPN and &quot;cisco_ipsec.ko&quot;"
date: 2008-08-07
forum: General Help
---

### Post by Carlbc18 on 2008-08-07
I ran the ./vpn_install and i received this error:


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
make -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/usr/local/vpn/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /usr/local/vpn/vpnclient/linuxcniapi.o
/usr/local/vpn/vpnclient/linuxcniapi.c:12:26: error: linux/config.h: No such file or directory
/usr/local/vpn/vpnclient/linuxcniapi.c: In function ‘CniInjectReceive’:
/usr/local/vpn/vpnclient/linuxcniapi.c:297: error: implicit declaration of function ‘skb_set_timestamp’
/usr/local/vpn/vpnclient/linuxcniapi.c:331: error: ‘struct sk_buff’ has no member named ‘nh’
/usr/local/vpn/vpnclient/linuxcniapi.c:332: error: ‘struct sk_buff’ has no member named ‘mac’
/usr/local/vpn/vpnclient/linuxcniapi.c: In function ‘CniInjectSend’:
/usr/local/vpn/vpnclient/linuxcniapi.c:454: error: ‘struct sk_buff’ has no member named ‘mac’
/usr/local/vpn/vpnclient/linuxcniapi.c:455: error: ‘struct sk_buff’ has no member named ‘nh’
/usr/local/vpn/vpnclient/linuxcniapi.c:458: error: ‘struct sk_buff’ has no member named ‘h’
/usr/local/vpn/vpnclient/linuxcniapi.c:458: error: ‘struct sk_buff’ has no member named ‘nh’
make[2]: *** [/usr/local/vpn/vpnclient/linuxcniapi.o] Error 1
make[1]: *** [_module_/usr/local/vpn/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".


I understand the error has to do with the kernel headers, but i verified in the /usr/src/ that I have the 2.6.24-19-generic package.  I tried running patch <  vpnclient. . . .  stuff that was out on google, but to no avail.  If someone could help me out that owuld be greatly appreciated!!!!!

Regards-
B

---

### Post by tamoneya on 2008-08-07
two things:
1.  Is this a 32 bit or 64 bit OS?
2.  Do you have the build-essential package installed?

---

### Post by Carlbc18 on 2008-08-07
1) 32 bit
2) How do i tell if I have the build-essentials installed?

---

### Post by Carlbc18 on 2008-08-07
I downloaded the build-essentials package, but that uninstalls the linux-headers -- if I understand the error correctly i'm missing the kernel-headers. I should need that headers file, right?

---

### Post by linux_tech on 2008-08-07
Do you need Cisco client or could you use vpnc instead

 sudo apt-get install vpnc

---

### Post by linux_tech on 2008-08-07
1. Place your latest Cisco Client in your home directory.
2. Do a sudo apt-get install build-essential
3. Do a sudo apt-get install gcc
4. Do a uname -r to find the correct kernel-headers for your build.
5. Use synaptic to search and install the correct kernel-HEADERS, not source.
6. Untar your Cisco Client, go to the vpnclient folder and do a sudo sh vpn_install
7. Answer all questions, the defaults worked for me.
8. make sure you start the vpn sub-system with
sudo /etc/init.d/vpnclient_init start
9. Copy your .pcf profile to the sudo cp <your .pcf> /etc/opt/cisco-vpnclient/Profiles.
10. Do a vpnclient connect <your profile> (without the .pcf extention)

---

### Post by Carlbc18 on 2008-08-08
> **linux_tech said:**
> Do you need Cisco client or could you use vpnc instead

 sudo apt-get install vpnc


I need the Cisco client its work related.  I'll do the steps your provided above.  Thanks!

---

### Post by Carlbc18 on 2008-08-08
> **linux_tech said:**
> 1. Place your latest Cisco Client in your home directory.
2. Do a sudo apt-get install build-essential
3. Do a sudo apt-get install gcc
4. Do a uname -r to find the correct kernel-headers for your build.
5. Use synaptic to search and install the correct kernel-HEADERS, not source.
6. Untar your Cisco Client, go to the vpnclient folder and do a sudo sh vpn_install
7. Answer all questions, the defaults worked for me.
8. make sure you start the vpn sub-system with
sudo /etc/init.d/vpnclient_init start
9. Copy your .pcf profile to the sudo cp <your .pcf> /etc/opt/cisco-vpnclient/Profiles.
10. Do a vpnclient connect <your profile> (without the .pcf extention)

1) Done
2) latest already installed
3) latest already installed
4) uname -r = 2.6.24-19-generic
5) synaptic said it was already installed - i marked it for reinstallation.
6) sudo sh vpn_install
Cisco Systems VPN Client Version 4.8.00 (0490) Linux Installer
Copyright (C) 1998-2005 Cisco Systems, Inc. All Rights Reserved.

By installing this product you agree that you have read the
license.txt file (The VPN Client license) and will comply with
its terms. 

vpn_install: 47: Syntax error: "(" unexpected


Let me know if i should have done sudo ./vpn_install instead. 

Thanks.

---

### Post by Carlbc18 on 2008-08-08
Also, if I do sudo ./vpn_install I get the same error I originally reported.

---

### Post by linux_tech on 2008-08-09
go here: [http://160.78.48.20/vpn/software/Linux/](http://160.78.48.20/vpn/software/Linux/)
install this version: vpnclient-linux-x86_64-4.8.01.0640-k9.tar.gz 21-May-2008 17:45  2.0M 

make a new directory, extract the files to it and cd to it, then type

 sudo ./vpn_install

this should install the client (it worked for me)

* You may wish to change these permissions to restrict access to root.
* You must run "/etc/init.d/vpnclient_init start" before using the client.
* This script will be run AUTOMATICALLY every time you reboot your computer.

It looks like this file is a better 
version than the previous, w/ less hoops to jump thru 
This should resolve the earlier issue w/ error Failed to make module "cisco_ipsec.ko" and various other errors.

This page : [http://www.blog.arun-prabha.com/2006/11/16/installing-cisco-vpn-and-vpnc-in-ubuntu/](http://www.blog.arun-prabha.com/2006/11/16/installing-cisco-vpn-and-vpnc-in-ubuntu/)
has info on installing vpnc and how to download the <filename>.pcf file from your company. .pcf (file with the profile information that helps you to connect to your company's server, if applicable to your situ.)

---

### Post by Carlbc18 on 2008-08-09
Hi Linux_Tech - Thank you for the good information, but unfortunately, I am still having a similar problem. 

/CiscoVpn/vpnclient$ sudo ./vpn_install
Cisco Systems VPN Client Version 4.8.01 (0640) Linux Installer
Copyright (C) 1998-2006 Cisco Systems, Inc. All Rights Reserved.

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
make -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/home/bcarlson/CiscoVpn/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /home/bcarlson/CiscoVpn/vpnclient/linuxcniapi.o
In file included from /home/bcarlson/CiscoVpn/vpnclient/Cniapi.h:15,
                 from /home/bcarlson/CiscoVpn/vpnclient/linuxcniapi.c:31:
/home/bcarlson/CiscoVpn/vpnclient/GenDefs.h:113: error: conflicting types for &#8216;uintptr_t&#8217;
include/linux/types.h:40: error: previous declaration of &#8216;uintptr_t&#8217; was here
make[2]: *** [/home/bcarlson/CiscoVpn/vpnclient/linuxcniapi.o] Error 1
make[1]: *** [_module_/home/bcarlson/CiscoVpn/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".


I will take a look at that other vpn software. I have the .pcf from my company, but i'm not sure if that will be supported. :(

---

### Post by linux_tech on 2008-08-09
Sounds like it still doesn't like the kernal headers
The newer version from the link in my previous post is supposed to compile on all the new 2.6.xx kernels without the need for patching! 

You can also try the patch
Installation instructions:

1. Untar the VPN Client
# tar xzf vpnclient-linux-4.8.00.0490-k9.tar.gz

2. Download the patch
# wget -q [http://tuxx-home.at/projects/cisco-vpnclient/vpnclient-linux-2.6.22.diff](http://tuxx-home.at/projects/cisco-vpnclient/vpnclient-linux-2.6.22.diff)

3. Change to the vpnclient directory
# cd vpnclient

4. Apply the patch
# patch <../vpnclient-linux-2.6.22.diff
patching file frag.c
patching file interceptor.c
patching file IPSecDrvOS_linux.c
patching file linuxcniapi.c
patching file linux_os.h

Now the patch has been applied and you can safely install the client

# Next we actually build the Cisco VPN client, issue this command:
$ sudo ./vpn_install
Just hit enter for everything it asks you, the defaults are all OK. You may see lots of warnings, but those are OK.
# The VPN client is installed, now we need to start it:
$ sudo /etc/init.d/vpnclient_init start
# Place your .pcf configuration files in /etc/opt/cisco-vpnclient/Profiles/
# If your .pcf file is called myVPN.pcf, you&#8217;ll connect to the VPN with the following command:
$ sudo vpnclient connect myVPN
-----------------------------------------------------------------------------------
Alternately if you decide to use vpnc, you may also be interested in the resolvconf package. This helps in keeping /etc/resolv.conf in sync with the network connection chosen.

---

### Post by realgt on 2009-08-28
> **Carlbc18 said:**
> 1) Done
2) latest already installed
3) latest already installed
4) uname -r = 2.6.24-19-generic
5) synaptic said it was already installed - i marked it for reinstallation.
6) sudo sh vpn_install
Cisco Systems VPN Client Version 4.8.00 (0490) Linux Installer
Copyright (C) 1998-2005 Cisco Systems, Inc. All Rights Reserved.

By installing this product you agree that you have read the
license.txt file (The VPN Client license) and will comply with
its terms. 

vpn_install: 47: Syntax error: "(" unexpected


Let me know if i should have done sudo ./vpn_install instead. 

Thanks.

you're step 6 should've been

sudo ./vpn_install

instead of sudo sh ./vpn_install

---

