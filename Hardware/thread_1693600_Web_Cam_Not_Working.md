---
title: "Web Cam Not Working"
date: 2011-02-23
forum: Hardware
---

### Post by cstorvold on 2011-02-23
I've spent hours searching for a solution.  Webcam doesn't work in any programs and light stays off - Cheese, Skype, VLC.

Ubuntu 10.10
Acer Aspire 5630
Logitech OrbiCam (integrated)

/dev/video0 exists

lsusb output:

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 008: ID 046d:0896 Logitech, Inc. OrbiCam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

lspci output:

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300] (rev a1)
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
06:01.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
06:04.2 SD Host controller: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
06:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
06:04.4 FLASH memory: ENE Technology Inc SD/MMC Card Reader Controller (rev 01)

lsmod | grep gspca output:

gspca_vc032x        24745  0 
gspca_main           23644  1 gspca_vc032x
videodev               43098  1 gspca_main

lsmod | grep video output:

videodev                      43098  1 gspca_main
v4l1_compat            13359  1 videodev
video                                18712   0 
output                             1883      1 video



Thanks

I installed MPlayer and got it to turn the green cam light on but no video.  Light will not turn off and MPlayer will not quit.

---

### Post by kvarley on 2011-02-23
I found a thread relating to your webcam and updates within Ubuntu.

> i have seen in past few mouth's some have had to reinstall gspca

See the thread here: [http://ubuntuforums.org/showthread.php?p=10481090]("http://ubuntuforums.org/showthread.php?p=10481090")

---

### Post by cstorvold on 2011-02-23
How would I reinstall gspca?

---

### Post by pjrodz on 2011-05-18
i have the same laptop model running ubuntu 11.04. unfortunately, i'm having the same problems with the webcam. hope somebody could help us on this one. thanks!

---

### Post by pjrodz on 2011-05-19
> **cstorvold said:**
> How would I reinstall gspca?

this worked for me :D

[http://stemp.wordpress.com/2009/11/03/karmic-get-the-latest-drivers-for-gspca-uvc-usbvideo-and-other/]("http://stemp.wordpress.com/2009/11/03/karmic-get-the-latest-drivers-for-gspca-uvc-usbvideo-and-other/")

---

