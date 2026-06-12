---
title: "External HDD not mounting on boot (at times)"
date: 2018-05-08
forum: Hardware
---

### Post by Automat2 on 2018-05-08
Hello,
I have a new problem since the upgrade to Bionic and it's that my external HDD doesn't seem to mount at boot as it should.
For the last two or three times I started this box,  I had to unplug-replug the power and/or the USB wire for Ubuntu to detect and mount the HDD unit.
I've had the HDD for almost two years, and with older versions of Ubuntu had some mounting problems, but now they are increasing in frequency.
The HDD needs external power and the USB plugs at both ends. I can't see a problem with loose connections.
This is the lsusb output -now that it has mounted correctly.
```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 007: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 006: ID 03f0:d711 Hewlett-Packard 
Bus 001 Device 005: ID 041e:4093 Creative Technology, Ltd 
Bus 001 Device 008: ID 08bb:2900 Texas Instruments PCM2900 Audio Codec
Bus 001 Device 003: ID 0a12:0001 CamBus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 007: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 006: ID 03f0:d711 Hewlett-Packard 
Bus 001 Device 005: ID 041e:4093 Creative Technology, Ltd 
Bus 001 Device 008: ID 08bb:2900 Texas Instruments PCM2900 Audio Codec
Bus 001 Device 003: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 001 Device 002: ID 050d:0307 Belkin Components USB 2.0 - 7 ports Hub [FSU307]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 002: ID 04e8:6123 Samsung Electronics Co., Ltd 
Bus 007 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
bridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 001 Device 002: ID 050d:0307 Belkin Components USB 2.0 - 7 ports Hub [FSU307]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 002: ID 04e8:6123 Samsung Electronics Co., Ltd 
Bus 007 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
Does anybody know how to make the mounting of this HDD work by default at startup? Or does anybody know why is not mounting at times?
Thanks.

---

### Post by #&amp;thj^% on 2018-05-08
I have also seen what you are experiencing since kernel 4.15 and newer.
It seems in my case if I opened "gnome-disk-utility" and clicked on the effected Disk or partition, and then below the window you will see a double cog, select that>>>choose "Edit Mount Option"
Then deselected the "Default Session Default" >>>Then checked the box "Mount at system startup"
And yes that Drive is also a USB external drive.
```
$ pinxi --usb
USB:
  Hub: 1:1 usb: 2.0 type: Full speed (or root) hub 
  Device-1: Logitech Unifying Receiver bus ID: 1:2 type: Keyboard 
  Device-2: Realtek Mass Storage Device bus ID: 1:3 type: Mass Storage 
  Device-3: Intel bus ID: 1:4 type: Bluetooth 
  Device-4: Linksys WUSB100 v1 RangePlus Wireless Network Adapter [Ralink 
  RT2870] 
  bus ID: 1:5 type: Vendor Specific Protocol 
  Device-5: JMicron / JMicron USA ATA/ATAPI Bridge bus ID: 1:6 
  type: Mass Storage 
  Hub: 1:15 usb: 1.0 type: Genesys Logic USB 1.1 Hub 
  Device-6: Logitech Unifying Receiver bus ID: 1:16 type: Keyboard 
  Hub: 2:1 usb: 3.0 type: Full speed (or root) hub 
  Device-7: ASMedia ASM1051E SATA 6Gb/s bridge ASM1053E SATA 6Gb/s bridge 
  ASM1153 SATA 3Gb/s bridge 
  bus ID: 2:2 type: Mass Storage 

```
And my disk layout:
```
pinxi --D
Drives:
  HDD Total Size: 4.55 TiB used: 373.06 GiB (8.0%) 
  ID-1: /dev/sda vendor: Western Digital model: WD1001FALS-00J7B0 
  size: 931.51 GiB 
  ID-2: /dev/sdb vendor: Western Digital model: WD5000AAKS-00V1A0 
  size: 465.76 GiB 
  ID-3: /dev/sdc type: USB vendor: Western Digital model: WD5000BPVT-00HXZT1 
  size: 465.76 GiB 
  ID-4: /dev/sde type: USB model: EZEX-60WN4A0 size: 931.51 GiB 
  ID-5: /dev/sdf type: USB vendor: Western Digital model: WD10EZEX-60WN4A0 
  size: 1.82 TiB 

```
Screenshot also to help.

---

