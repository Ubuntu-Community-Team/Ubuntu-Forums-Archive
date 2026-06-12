---
title: "CHEESE: no picture/video"
date: 2008-12-15
forum: Hardware
---

### Post by rugbeeprop on 2008-12-15
Hi,

I am a bit confused after reading through a few posts and blogs on the internet regarding Cheese and Webcam.

I have HP Pavillion DV9616CA (DV9000 series), running Ubuntu 8.10. I have been able to use Cheese to capture Picture/Video from the built-in webcam. The last time I took a picture using Cheese was about two weeks ago. I ran Cheese again earlier and it displayed a blank screen (the webcam light was on). 

On one of many posts I read, the suggestion was to test the webcam using Ekiga. Ekiga was able to display the picture from the webcam.

I also tried to test it with Camorama and it was not able to detect any webcam (video01 - I think).

Here is the output of lsub:
```
Bus 007 Device 002: ID 064e:a101 Suyin Corp. 
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```and here is the output of lscpi:
```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
07:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
07:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
07:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
07:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
07:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
```Also, I hope this maybe helpful as well. This is the output on Command Line when I run it from Terminal:
```
(cheese:8775): GStreamer-WARNING **: pad source:src returned caps which are not a real subset of its template caps

(cheese:8775): GStreamer-WARNING **: pad source:src returned caps which are not a real subset of its template caps

(cheese:8775): GStreamer-WARNING **: pad video_source:src returned caps which are not a real subset of its template caps
libv4l2: error converting / decoding frame data: v4l-convert: error destination buffer too small

```Any help to shed a light to this will be much appreciated. Thanks.

---

### Post by rugbeeprop on 2008-12-16
So what do you know? I started the post and now I resolved it myself :)

Here is how I solved it: [https://bugs.edge.launchpad.net/ubuntu/+source/libv4l/+bug/282473/comments/22](https://bugs.edge.launchpad.net/ubuntu/+source/libv4l/+bug/282473/comments/22)

The main Bug page is [https://bugs.launchpad.net/ubuntu/+source/libv4l/+bug/282473](https://bugs.launchpad.net/ubuntu/+source/libv4l/+bug/282473)

---

### Post by holr on 2008-12-20
Thanks! Having the exact same problem, came across your post, problem no more. (using a macbook pro 3,1 revision with builtin isight)

---

