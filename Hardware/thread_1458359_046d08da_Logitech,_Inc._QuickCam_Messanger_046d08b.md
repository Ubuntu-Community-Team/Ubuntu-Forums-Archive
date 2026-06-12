---
title: "046d:08da Logitech, Inc. QuickCam Messanger 046d:08b2 Logitech, Inc. QuickCam Pro"
date: 2010-04-19
forum: Hardware
---

### Post by internaciulo on 2010-04-19
Hello,

I have two Logitech webcam and neither works

Here's what I've done

Any pointer for help ?


$ sudo bash

$ cat /etc/*release*
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.10
DISTRIB_CODENAME=karmic
DISTRIB_DESCRIPTION="Ubuntu 9.10"

$ uname -a
Linux 87rueMozart 2.6.31-20-generic-pae #58-Ubuntu SMP Fri Mar 12 06:25:51 UTC 2010 i686 GNU/Linux

$ lsusb
Bus 002 Device 008: ID 10d5:55a2 Uni Class Technology Co., Ltd 2Port KVMSwitcher
Bus 002 Device 007: ID 1e54:2030  
Bus 002 Device 006: ID 046d:c063 Logitech, Inc. 
Bus 002 Device 005: ID 058f:9254 Alcor Micro Corp. Hub
Bus 002 Device 004: ID 0d62:2106 Darfon Electronics Corp. 
Bus 002 Device 003: ID 03f0:4811 Hewlett-Packard PSC 1600
Bus 002 Device 002: ID 0955:000a NVidia Corp. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[B]Bus 001 Device 020: ID 046d:08da Logitech, Inc. QuickCam Messanger
Bus 001 Device 019: ID 046d:08b2 Logitech, Inc. QuickCam Pro 4000[/B]
Bus 001 Device 018: ID 11b0:6148 ATECH FLASH TECHNOLOGY 
Bus 001 Device 015: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 011: ID 059b:047a Iomega Corp. 
Bus 001 Device 002: ID 04b4:6560 Cypress Semiconductor Corp. CY7C65640 USB-2.0 "TetraHub"
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

$ lsmod | grep pwc
pwc                    81632  0 
videodev               36736  2 gspca_main,pwc

$ dmesg | grep -i quickcam
[177134.096638] pwc: Also supports the Askey VC010, various Logitech Quickcams, Samsung MPC-C10 and MPC-C30,
[177134.096674] pwc: Logitech QuickCam 4000 Pro USB webcam detected.
[181945.397214] pwc: Logitech QuickCam 4000 Pro USB webcam detected.

$ apt-cache show skype
Package: skype
Status: install ok installed
Priority: extra
Section: non-free/net
Installed-Size: 25579
Maintainer: Skype Technologies <info@skype.net>
Architecture: i386
Version: 2.1.0.81-1
Depends: libasound2 (>> 1.0.17), libc6 (>= 2.7-1), libgcc1 (>= 1:4.3), libqt4-dbus (>= 4.4.3), libqt4-network (>= 4.4.3), libqtcore4 (>= 4.4.3), libqtgui4 (>= 4.4.3), libstdc++6 (>= 4.3), libx11-6, libxext6, libxss1, libxv1
Conffiles:
 /etc/dbus-1/system.d/skype.conf d09fd2adb2487dbaaeb97c43f6cdc08d
Description: Skype
 .
 Skype is a little piece of software that lets you make free calls to anyone else on Skype,
 anywhere in the world. And even though the calls are free, they are really excellent quality.
 .
 * Make free Skype-to-Skype calls to anyone else, anywhere in the world.
 * Call phones and mobiles at pretty cheap rates per minute.
 * Group chat with up to 100 people or conference call with up to nine others.
 * Free to download.

$ sudo apt-get install xawtv

jmfayard@87rueMozart:/media/FJ_FAYARD/Contacts$ xawtv -c /dev/video0
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.31-20-generic-pae)
xinerama 0: 1920x1080+0+0
WARNING: No DGA direct video mode for this display.
/dev/video0 [v4l2]: no overlay support
v4l-conf had some trouble, trying to continue anyway
Warning: Missing charsets in String to FontSet conversion
Warning: Cannot convert string "-*-lucidatypewriter-bold-r-normal-*-14-*-*-*-m-*-iso8859-*,           -*-courier-bold-r-normal-*-14-*-*-*-m-*-iso8859-*,          -gnu-unifont-bold-r-normal--16-*-*-*-c-*-*-*,        -efont-biwidth-bold-r-normal--16-*-*-*-*-*-*-*,                 -*-*-bold-r-normal-*-16-*-*-*-m-*-*-*,                 -*-*-bold-r-normal-*-16-*-*-*-c-*-*-*,                         -*-*-*-*-*-*-16-*-*-*-*-*-*-*,*" to type FontSet
Warning: Cannot convert string "-*-ledfixed-medium-r-*--39-*-*-*-c-*-*-*" to type FontStruct
Warning: Missing charsets in String to FontSet conversion
Warning: Cannot convert string "-*-lucidatypewriter-bold-r-normal-*-14-*-*-*-m-*-iso8859-*,           -*-courier-bold-r-normal-*-14-*-*-*-m-*-iso8859-*,          -gnu-unifont-bold-r-normal--16-*-*-*-c-*-*-*,        -efont-biwidth-bold-r-normal--16-*-*-*-*-*-*-*,                 -*-*-bold-r-normal-*-16-*-*-*-m-*-*-*,                 -*-*-bold-r-normal-*-16-*-*-*-c-*-*-*,                         -*-*-*-*-*-*-16-*-*-*-*-*-*-*, *" to type FontSet


Does not work !

Skype does not work !

---

