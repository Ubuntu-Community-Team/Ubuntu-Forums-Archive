---
title: "Connect to Internet Using Router and LAN Port"
date: 2005-12-05
forum: General Help
---

### Post by ZedLord on 2005-12-05
I Dual-Boot WinXP and Ubuntu 5.10 64Bit,
I Connect to Internet Using a ADSL Router Connected to LAN Port Of My System.
I Use the Following Parameters in WinXP

**IP**- 192.168.1.10
**Subnet**- 255.255.255.0
**Gateway**- 192.168.1.1
**Pri. DNS**- 203.145.184.13
**Sec. DNS**- 202.56.250.5

I Used the Same in the Network Options in Ubuntu, I Cant Seem to Connect to Internet.

I Cant Even Ping the Gateway (but I Can Ping the IP Address)
It Gives an error that the Host is Unreachable

When i type "ifconfig eth0" , I Get

> subbu@Subbu:/home$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:0B:6A:CF:DE:B7
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20b:6aff:fecf:deb7/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1140 (1.1 KiB)  TX bytes:537 (537.0 b)
          Interrupt:17 Base address:0xe400

Please Help Me. to Get the Internet Working.

I Even Tried to Install the Drivers of my Onboard Lan using the Drivers I Downloaded from the Manufacturer Website.

**The Readme File Says :**

        > ------------------------------------------------------------------------------------
          ULi M5263 10/100M Ethernet Controller Driver for kernel 2.6.x
        ------------------------------------------------------------------------------------

                    Copyright (c) 2004-2005, ULi Electronics Inc.
         

------------------
CONTENTS
------------------
1. ULi M5263 10/100M Ethernet Controller Core
2. File Signature
3. Installation Guide 
4. Revision History
5. Disclaimer


1. ULi M5263 10/100M Ethernet Controller Core
============================================= 
You can use command
        /sbin/lspci -n 
    or
        cat /proc/pci | grep 5263
to determine whether ULi M5263 Ethernet controller exists in your 
system. If yes, simply follow the steps below to install the driver.

This driver is dedicated to support ULi M5263 10/100M Ethernet 
Controller under Linux platform.

Any improper use of this module, such as combining it with different 
hardware and/or software environment, may produce unpredicable results.
The author of the driver and its property owner do not have 
responsibility for any property lose or damage.


2. File Signature
====================
/driver/uli526x.c	           source codec c file
readme.txt                            this file
====================
/sample/Kconfig.in                 configuration sample file
/sample/Makefile.in                sample makefile

3.Installation Guide
====================
To install the driver, you should reconfigure and recompile your Linux 
kernel as follows:

Make sure your kernel version number is 2.6.x.

Copy uli526x.c to /usr/src/linux-2.6.x/drivers/net/tulip/, and modify the
following file in this directory. (Make a backup of them.)

1.Kconfig.in
add the following lines to Kconfig.in file.(refer to the Kconfig.in file we provide to you)

config ULI526X
	tristate "ULi M526x controller support"
	depends on NET_TULIP && PCI
	select CRC32
	---help---
	  This driver is for ULi M5261/M5263 10/100M Ethernet Controller
	  (<http://www.uli.com.tw/>).

	  To compile this driver as a module, choose M here.

2.Makefile
add the following lines to Makefile.(refer to the Makefile we provide to you)

obj-$(CONFIG_ULI526X)	+= uli526x.o
------------------------------------
Install as a kernel module
------------------------------------

  Step 1: 
        Change directory to /usr/src/linux-2.6.x
        Use the command "make menuconfig" or "make xconfig", and make 
        sure "ULi M526x controller support" is set as module.
	
	Example:	
	Select "Device Drivers"
        Select "Networking support"
        Select "Ethernet (10 or 100Mbit)"
	Select "Tulip family network device support"
	Unselect "DECchip Tulip (dc2114x) PCI support"
        Select "ULi M526x controller support" as "m"

  Step 2:
        Select "Loadable module support", and unselect "Set version information
        on all module symbols"
	
	Before exit, save your configration.


  Step 3:
	make modules
	make modules_install

  Step 4:
	rmmod tulip
        modprobe uli526x	

 Then, you can bind any protocol into M5263 driver and use it.

------------------------------------------
Install as a part of linux kernel
------------------------------------------

  Step 1:
        Change directory to /usr/src/linux-2.6.x
        Use the command "make menuconfig" or "make xconfig", and make 
        sure "ULi M526x controller support" is set as kernel.
	
	Example:	
	Select "Device Drivers"
        Select "Networking support"
        Select "Ethernet (10 or 100Mbit)"
	Select "Tulip family network device support"
	Unselect "DECchip Tulip (dc2114x) PCI support"
        Select "ULi M526x controller support" as "y"
	

  Step 2:
        Select "Loadable module support", and unselect "Set version information
        on all module symbols"
	
	Before exit, save your configration.


  Step 3:
	make
	cp arch/i386/boot/bzImage /boot

  Step 4:
	If you use grub to boot your linux, then
	  1) Modify the file /etc/grub.conf by adding
		title 2.6.x
		root (hd0,2)
		kernel /boot/bzImage ro root=/dev/hd1
		The disk partition where your linux resides in, 
                for example: /dev/hda1
	  2) Reboot and select the kernel 2.6.x 
  
 Then, you can bind any protocol into M5263 driver and use it.


4. Revision History
===================
         V0.90	- First release. 
	 V0.91  - Change the all ali string to uli string and add the support to ethtool
	 V0.92	- Change the timeout length for UDP test
	 V0.93  - Change the tx queue count for UDP test,add non-srom solution

5. Disclaimer
=============
Product names used in this file are for identification purposes only 
and may be trademarks of their respective owners.

No part of this file may be copied or reproduced without written 
consent from ULi Electronics.

ULi Electronics makes no warranty for the use of its products and 
assumes no responsibility for any errors which may appear in this file 
nor does it make a commitment to update the information contained 
herein.

ULi Electronics retains the right to make changes to these 
specifications at any time, without notice.




[B]I'm Trying to Install the Driver as Kernel Module, But When I enter "make modules" I Get :
[/B]


> subbu@Subbu:/usr/src/linux-headers-2.6.12-9-amd64-k8$ sudo make modules
  CHK     include/linux/version.h
  UPD     include/linux/version.h
  SPLIT   include/linux/autoconf.h -> include/config/*
  CC      scripts/mod/empty.o
  MKELF   scripts/mod/elfconfig.h
  HOSTCC  scripts/mod/file2alias.o
  HOSTCC  scripts/mod/modpost.o
  HOSTCC  scripts/mod/sumversion.o
  HOSTLD  scripts/mod/modpost
make[1]: *** No rule to make target `arch/x86_64/kernel/msr.c', needed by `arch/x86_64/kernel/msr.o'.  Stop.
make: *** [arch/x86_64/kernel] Error 2


Please Help Me Here too. Thanks in Advance.
(PS- Please Provide the Link, If the Problem is Otherwise Solved in Another Post by a Different Person / Different Forum)

---

### Post by ZedLord on 2005-12-05
C'mon PPL! Help Me

**(BUMP)!**

---

### Post by grumpymole on 2005-12-05
See entry below.

---

### Post by grumpymole on 2005-12-05
When you log into Ubuntu,

1.  Do you have the Network Connection applet running in the top right-hand panel?  
2.  If you hover the mouse over it, which connection does it show in the tool-tip?  lo or eth0?
3.  If you go to System --> Administration --> Networking, does it show eth0 as active?  If not, activate it using the button in the applet.
4.  Have you tried using DHCP?

Regards

Warren

---

### Post by ZedLord on 2005-12-05
I Cant Connect Using DHCP!

and I Since I'm a NooB i Made a Stupid Mistake!

i typed "rmmod tulip"

now even eth0 is not available!

please help me install the Drivers!!

---

### Post by grumpymole on 2005-12-05
Try

sudo modprobe tulip

to re-install it.

Regards

Warren

---

