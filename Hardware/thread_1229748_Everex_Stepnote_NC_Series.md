---
title: "Everex Stepnote NC Series"
date: 2009-08-02
forum: Hardware
---

### Post by Im Jake on 2009-08-02
Anyways, I have a off brand laptop with off brand parts. But for the most part its a OK laptop. Well, It runs vista very poorly so I went with what every person would do Linux. Well, since all the parts are off brand in it (By the way its a Everex Stepnote NC Series Ver 2.0) its hard to find the drivers and much less for Linux. Well, I can't really get the sound working.. So I was wondering if there's a way you can help me. The video is really blocky, I can't get the wireless card working and I can't find anything else.

```
linux@linux-laptop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge (rev 80)
00:00.1 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. CN896/VN896/P4M900 I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Security Device
00:00.7 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. CN896/VN896/P4M900 PCI to PCI Bridge Controller
00:03.0 PCI bridge: VIA Technologies, Inc. CN896/VN896/P4M900 PCI to PCI Bridge Controller (rev 80)
00:0f.0 IDE interface: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 PCI bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
01:00.0 VGA compatible controller: VIA Technologies, Inc. CN896/VN896/P4M900 [Chrome 9 HC] (rev 01)
04:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)
05:01.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
linux@linux-laptop:~$
```

---

### Post by Im Jake on 2009-08-03
Bump

---

### Post by Im Jake on 2009-08-05
Bump

---

### Post by tgalati4 on 2009-08-05
I'm going to guess that you have a VIA processor as well.

What version of Linux or Ubuntu are you running?

For graphics, do a forum search on openchrome.

For wireless, do a forum search on atheros AR2413.

For sound, do a forum search on ?? who knows? 

I got Dapper Drake to run with some tweaking on a VIA-based mini-ATX machine a couple of years ago for a project.  The machine is not booted at the moment, so I can't recall what tweaks were required.  

I'm confident that you will get everything working eventually, but it will take some time and effort on your part.  Google and the forum search are your friends.

I'm sorry that I can't help further, but VIA-based machines are tricky to set up.  On the other hand last week I set up an IBM Thinkpad with an Intel chipset under Jaunty and everything worked out of the box.  So there is something to be said for a brand-name laptop with brand-name hardware.

Did this laptop come with Vista?

---

### Post by starcannon on 2009-08-06
I messed up and bought one of the Everex Cloudbooks.
The VIA GPU and CPU make these computers difficult, not impossible, but difficult.
You'll need to go here for some drivers/modules:
[http://linux.via.com.tw/support/downloadFiles.action](http://linux.via.com.tw/support/downloadFiles.action)

BTW the forum links at the linux.via.com.tw site are outdated; the new official via forums are at:
[http://www.viaarena.com/forums/forumdisplay.php?f=18](http://www.viaarena.com/forums/forumdisplay.php?f=18)
GL

---

### Post by Im Jake on 2009-08-07
Yes its a VIA processor, it came with linux..

I actually found out that the wireless card works without the drivers so I only need sound and video..

I also moved onto Fedora 11, but If needed I will switch back to ubuntu 9.04

---

### Post by Im Jake on 2009-08-08
As of now, I'm using the latest version of ubuntu :).

---

