---
title: "Acer Aspire 4310 with Broadcom (bcm43xx) and Realtek 268 Intel HDA Chipset"
date: 2007-09-03
forum: Hardware &amp; Laptops
---

### Post by Flyn on 2007-09-03
I just got this laptop recently, and I had a few problems with the wireless lan not working and no recording capability with the built in sound card. After looking into the matter with a lot of googling, I found the following solutions, I hope they will be helpful.

1.Broadcom (bcm43xx) Driver:
 (shamelessly copied from [http://premrara.blogspot.com/](http://premrara.blogspot.com/))

The Ubuntu Linux version is:

$ cat /etc/issue.net
Ubuntu 7.04
The Linux kernel version is:
$ uname -a
Linux xxx-laptop 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686 GNU/Linux

The fresh install will detect the WLAN hardware but will fail on initialization (use dmesg to see kernel messages):
$ dmesg
bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
atkbd.c: Unknown key pressed (translated set 2, code 0xd4 on isa0060/serio0).
atkbd.c: Use 'setkeycodes e054 ' to make it known.
The first line looks for the Broadcom firmware. The second and third lines is a response to pressing the Bluetooth key.

The following is the output of lspci:
$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller AHCI (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
03:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)
0a:06.0 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
0a:06.2 Generic system peripheral [0805]: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02)
0a:06.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)

First, install bcm43xx-fwcutter. fwcutter is a tool which can extract firmware from various source files. It's written for BCM43xx driver files.
$ sudo aptitude install bcm43xx-fwcutter

You will get the following error message:
Preconfiguring packages ...
Selecting previously deselected package bcm43xx-fwcutter.
(Reading database ... 88014 files and directories currently installed.)
Unpacking bcm43xx-fwcutter (from .../bcm43xx-fwcutter_1%3a006-1_i386.deb) ...
Setting up bcm43xx-fwcutter (006-1) ...
--22:15:56--  [http://boredklink.googlepages.com/wl_apsta.o](http://boredklink.googlepages.com/wl_apsta.o)
           => `wl_apsta.o'
Resolving boredklink.googlepages.com... 72.14.203.118
Connecting to boredklink.googlepages.com|72.14.203.118|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
22:15:57 ERROR 404: Not Found.

dpkg: error processing bcm43xx-fwcutter (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 bcm43xx-fwcutter
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up bcm43xx-fwcutter (006-1) ...
--22:15:57--  [http://boredklink.googlepages.com/wl_apsta.o](http://boredklink.googlepages.com/wl_apsta.o)
           => `wl_apsta.o'
Resolving boredklink.googlepages.com... 72.14.203.118
Connecting to boredklink.googlepages.com|72.14.203.118|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
22:15:58 ERROR 404: Not Found.

dpkg: error processing bcm43xx-fwcutter (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 bcm43xx-fwcutter

Just proceed and download the firmware/driver:
$ wget [http://sidulus.textdrive.com/bcmwl5sys.zip](http://sidulus.textdrive.com/bcmwl5sys.zip)

mirror: [http://premrara.googlepages.com/bcmwl5sys.zip](http://premrara.googlepages.com/bcmwl5sys.zip)

Extract the firmware from the driver:
$ sudo bcm43xx-fwcutter -w /lib/firmware ~/Desktop/bcmwl5.sys

This will create lots of new files in the /lib/firmware directory, this is the firmware part of the driver that will make your card work with ubuntu!

Also put the driver in the kernel folder:
$ uname -r
2.6.20-15-generic
$ sudo bcm43xx-fwcutter -w /lib/firmware/2.6.20-15-generic ~/Desktop/bcmwl5.sys

Your WLAN card should now work!

2.   Realtek 268 Intel HDA Chipset ALSA Patch:
(shamelessly copied from user venky80 from [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/116326](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/116326))
1)Download alsa-drivers, alsa-firware, alsa-lib, alsa-util version 1.0.14 from ALSA.org and extract it into a directory named ALSA in desktop or your home
2) Replace patch_realtek.c and hda_proc.c in the ~ALSA/alsa-driver-1.0.14/alsa-kernel/pci/hda with the new files from [http://launchpadlibrarian.net/8552578/ha_realtek_parch_files.zip](http://launchpadlibrarian.net/8552578/ha_realtek_parch_files.zip)
 3) Then do sudo ./configure sudo make and sudo make install in the following folders according to the order specified (order is important) ALSA lib , ALSA utils ALSA firmware and lastly ALSA drivers.
hopefully you will see no errors.
4) restart 




Be sure to unmute your mixer.



Hope this helps, just thought to repost it here so it would be more accessible and would take fewer searches to find.

---

