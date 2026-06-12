---
title: "Toshiba satellite C885-1EL"
date: 2012-12-13
forum: Hardware
---

### Post by raouls on 2012-12-13
Hi !

I am new to ubuntu or you might say that ubuntu is new for me...the idea is that i have a Toshiba satellite C885-1EL laptop model,PSKCAE part number and after i have installed ubuntu 12.10, my ethernet card (Relatek RT8723AE Wireless LAN 802.11n PCI-E NIC) is not recognized.

what can i do?

is there any way for me to compile my own kernel and add to the kernel a Relatek driver?

i tried what i found here ([http://askubuntu.com/questions/139632/wireless-card-realtek-rtl8723ae-bt-is-not-recognized](http://askubuntu.com/questions/139632/wireless-card-realtek-rtl8723ae-bt-is-not-recognized)) but i did not managed do activate my ethernet card.

Please help me!

---

### Post by raouls on 2012-12-13
raoul@raoul-SATELLITE-C855-1EL:~$ sudo lshw -C network

  *-network UNCLAIMED
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: ioport:3000(size=256) memory:c2400000-c2403fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 05
       serial: 4c:72:b9:e5:18:4a
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8105e-1.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:42 ioport:2000(size=256) memory:c0004000-c0004fff memory:c0000000-c0003fff

raoul@raoul-SATELLITE-C855-1EL:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.10
Release:	12.10
Codename:	quantal

raoul@raoul-SATELLITE-C855-1EL:~$ uname -a
Linux raoul-SATELLITE-C855-1EL 3.5.0-17-generic #28-Ubuntu SMP Tue Oct 9 19:31:23 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

raoul@raoul-SATELLITE-C855-1EL:~$ sudo rfkill list
0: hci0: Bluetooth
 Soft blocked: no
 Hard blocked: no

Please help!!!

---

### Post by oldfred on 2012-12-14
I do not know details but a similar thread that seems to have some answers?

[http://ubuntuforums.org/showthread.php?t=1964200](http://ubuntuforums.org/showthread.php?t=1964200)

---

### Post by raouls on 2012-12-14
that did not helped me...
i tried & tried & tried again...nothing

---

### Post by raouls on 2012-12-14
this is what i get after trying to install the driver that works with my kernel version

raoul@raoul-SATELLITE-C855-1EL:~/Downloads$ sudo update-initramfs -u && cd ~/Downloads && tar xvf r8101-1.023.00.tar.bz2 && cd r8101-1.023.00 && sudo sh autorun.sh
update-initramfs: Generating /boot/initrd.img-3.5.0-17-generic
r8101-1.023.00/
r8101-1.023.00/src/
r8101-1.023.00/src/rtltool.h
r8101-1.023.00/src/rtl_eeprom.h
r8101-1.023.00/src/r8101.h
r8101-1.023.00/src/r8101_n.c
r8101-1.023.00/src/rtl_ethtool.h
r8101-1.023.00/src/rtl_eeprom.c
r8101-1.023.00/src/Makefile_linux24x
r8101-1.023.00/src/Makefile
r8101-1.023.00/src/rtltool.c
r8101-1.023.00/autorun.sh
r8101-1.023.00/readme
r8101-1.023.00/Makefile

Check old driver and unload it.
Build the module and install
make: *** /lib/modules/3.5.0-17-generic/build: No such file or directory.  Stop.
make[1]: *** [clean] Error 2
make: *** [clean] Error 2

what should i do now ??
please help me!

---

### Post by oldfred on 2012-12-14
Maybe you have the same issue we have on the video side. To correctly install the nvidia drivers I had to download headers. 
You will have to install from CD/DVD or flash drive as you do not have Internet.

       # You may need headers - meta package for current version:
sudo apt-get install linux-headers-generic

    
Then redo the commands for your Ethernet driver.

---

