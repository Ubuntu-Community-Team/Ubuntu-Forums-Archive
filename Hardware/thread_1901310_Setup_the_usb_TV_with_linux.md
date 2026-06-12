---
title: "Setup the usb TV with linux?"
date: 2011-12-28
forum: Hardware
---

### Post by honeybear on 2011-12-28
Hello,

I have bought a usb tv device.

```

[14719.895967] rox[331]: segfault at 9720002 ip 08099c88 sp bfcc1188 error 4 in rox[8048000+7c000]
[63636.039676] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[64511.077592] usb 1-1.1: USB disconnect, address 3
[89108.046416] usb 1-1.2: new high speed USB device using ehci_hcd and address 4
[89108.147884] usb 1-1.2: New USB device found, idVendor=0fd9, idProduct=002c
[89108.147890] usb 1-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[89108.147894] usb 1-1.2: Product: EyeTV DTT Dlx
[89108.147897] usb 1-1.2: Manufacturer: Elgato
[89108.147900] usb 1-1.2: SerialNumber: 000100504018157
[89108.148006] usb 1-1.2: configuration #1 chosen from 1 choice
tisom@ubuntopower:~$ lsusb
Bus 003 Device 007: ID 04f3:0216 Elan Microelectronics Corp.
Bus 003 Device 006: ID 03f0:2d12 Hewlett-Packard
Bus 003 Device 005: ID 045e:00b0 Microsoft Corp. Digital Media Pro Keyboard
Bus 003 Device 004: ID 046d:0807 Logitech, Inc. Webcam B500
Bus 003 Device 003: ID 0556:0001 Asahi Kasei Microsystems Co., Ltd AK5370 I/F A/D Converter
Bus 003 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[COLOR="Red"]**Bus 001 Device 004: ID 0fd9:002c Elgato Systems GmbH EyeTV DTT Deluxe v2**[/COLOR]
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
tisom@ubuntopower:~$ ls /dev/vid*
/dev/video0  /dev/video1
tisom@ubuntopower:~$ ls /dev/vid*



```

no new videoX shows into /dev/.  How to make this DVB-T to work please? 

video1 and video2 are my testing webcams. I shall get a video3, and tvtime cannot find any video3

thank you


No help either with 

>  modprobe em28xx

ls /dev/video*
/dev/video0  /dev/video1



uname -a
Linux 2.6.32-5-686-bigmem

---

### Post by tomlab on 2012-03-05
Hi honeybear,

Did you manage to solve the issue? I have exactly the same problem, but I didn't succeed in making my Eye TV DTT deluxe working. 
I've tried the solution mentionned to this post, without success: [http://ubuntuforums.org/showthread.php?t=1510188](http://ubuntuforums.org/showthread.php?t=1510188)
(changing the ID with 0x002c)...

---

### Post by honeybear on 2012-03-07
> **tomlab said:**
> Hi honeybear,

Did you manage to solve the issue? I have exactly the same problem, but I didn't succeed in making my Eye TV DTT deluxe working. 
I've tried the solution mentionned to this post, without success: [http://ubuntuforums.org/showthread.php?t=1510188](http://ubuntuforums.org/showthread.php?t=1510188)
(changing the ID with 0x002c)...

they said taht the kernel should see it and one gets /dev/dvb/0  or something stuffs into /dev

I am been said by the creator of DVB that it could be possible, .. but no idea how

you see the UBUNTU WIKI is bull****. They say that all hardwares work, but in practice it s mentioned crap. why to leave this pages alive, because it simply promotes linux hardware. since few users, then not so much issues


I bought 5 dvb pendrive and nothing worked.

---

