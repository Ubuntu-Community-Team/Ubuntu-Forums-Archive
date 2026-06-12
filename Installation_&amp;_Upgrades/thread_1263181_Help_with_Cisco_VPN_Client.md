---
title: "Help with Cisco VPN Client"
date: 2009-09-10
forum: Installation &amp; Upgrades
---

### Post by BURMAT on 2009-09-10
New here.. Just wanted to say this forum has provided me with so much help dealing with my problems. I just registered here because this is one problem I have not been able to solve by searching.

Before I am allowed to connect to my wireless here on campus, I have to download Cisco VPN client v4.6.00.045. The linux version of this is unsupported here though. I am running Ubuntu 9.04, GNOME 2.26.1, and Kernel 2.6.28-15-generic. I understand that there is a patch for Kernels 2.6+ but nothing seems to be working for me. I will post again the errors and everything I get from the failed install without the patch. Any help is greatly appreciated in advance.

-Nathan

---

### Post by BURMAT on 2009-09-10
USER@ubuntu:~$ cd Desktop/vpnclient 
 USER@ubuntu:~/Desktop/vpnclient$ sudo ./vpn_install 
 [sudo] password for USER:  
 Cisco Systems VPN Client Version 4.6.00 (0045) Linux Installer 
 Copyright (C) 1998-2004 Cisco Systems, Inc. All Rights Reserved. 

 By installing this product you agree that you have read the 

 license.txt file (The VPN Client license) and will comply with 
 its terms. 
  
 Directory where binaries will be installed [/usr/local/bin] 
  
 Automatically start the VPN service at boot time [yes] 
  
 In order to build the VPN kernel module, you must have the 
 kernel headers for the version of the kernel you are running. 
  
 Directory containing linux kernel source code [/lib/modules/2.6.28-15-generic/build] 
  
 * Binaries will be installed in "/usr/local/bin". 
 * Modules will be installed in "/lib/modules/2.6.28-15-generic/CiscoVPN". 
 * The VPN service will be started AUTOMATICALLY at boot time. 
 * Kernel source from "/lib/modules/2.6.28-15-generic/build" will be used to build the module.
  
 Is the above correct [y] 

 Making module 
 make -C /lib/modules/2.6.28-15-generic/build SUBDIRS=/home/USER/Desktop/vpnclient modules 
 make[1]: Entering directory `/usr/src/linux-headers-2.6.28-15-generic' 
   CC [M]  /home/USER/Desktop/vpnclient/linuxcniapi.o 
 /home/USER/Desktop/vpnclient/linuxcniapi.c:12:26: error: linux/config.h: No such file or directory 
 In file included from /home/USER/Desktop/vpnclient/Cniapi.h:15, 
                  from /home/USER/Desktop/vpnclient/linuxcniapi.c:34: 
 /home/USER/Desktop/vpnclient/GenDefs.h:114: error: conflicting types for ‘uintptr_t’ 
 include/linux/types.h:40: error: previous declaration of ‘uintptr_t’ was here 
 /home/USER/Desktop/vpnclient/linuxcniapi.c: In function ‘CniInjectReceive’: 
 /home/USER/Desktop/vpnclient/linuxcniapi.c:315: error: ‘struct sk_buff’ has no member named ‘stamp’ 
 /home/USER/Desktop/vpnclient/linuxcniapi.c:347: error: ‘struct sk_buff’ has no member named ‘nh’ 
 /home/USER/Desktop/vpnclient/linuxcniapi.c:348: error: ‘struct sk_buff’ has no member named ‘mac’ 
 /home/USER/Desktop/vpnclient/linuxcniapi.c: In function ‘CniInjectSend’: 
 /home/USER/Desktop/vpnclient/linuxcniapi.c:452: error: ‘struct sk_buff’ has no member named ‘stamp’ 
 /home/USER/Desktop/vpnclient/linuxcniapi.c:456: error: ‘struct sk_buff’ has no member named ‘mac’ 
 /home/USER/Desktop/vpnclient/linuxcniapi.c:457: error: ‘struct sk_buff’ has no member named ‘nh’ 
 /home/USER/Desktop/vpnclient/linuxcniapi.c:460: error: ‘struct sk_buff’ has no member named ‘h’ 
 /home/USER/Desktop/vpnclient/linuxcniapi.c:460: error: ‘struct sk_buff’ has no member named ‘nh’ 
 make[2]: *** [/home/USER/Desktop/vpnclient/linuxcniapi.o] Error 1 
 make[1]: *** [_module_/home/USER/Desktop/vpnclient] Error 2 
 make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-15-generic' 
 make: *** [default] Error 2 
 Failed to make module "cisco_ipsec.ko". 
 USER@ubuntu:~/Desktop/vpnclient$ [http://ubuntuforums.org/showthread.php?t=1052065](http://ubuntuforums.org/showthread.php?t=1052065)

---

