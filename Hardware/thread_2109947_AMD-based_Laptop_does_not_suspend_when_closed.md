---
title: "AMD-based Laptop does not suspend when closed"
date: 2013-01-28
forum: Hardware
---

### Post by jcobban on 2013-01-28
I have a relatively new Dell laptop.  lspci returns:

00:00.0 Host bridge: Advanced Micro Devices [AMD] Family 12h Processor Root Complex
00:01.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI BeaverCreek [Mobility Radeon HD 6620G]
00:01.1 Audio device: Advanced Micro Devices [AMD] nee ATI BeaverCreek HDMI Audio [Radeon HD 6500D and 6400G-6600G series]
00:04.0 PCI bridge: Advanced Micro Devices [AMD] Family 12h Processor Root Port
00:06.0 PCI bridge: Advanced Micro Devices [AMD] Family 12h Processor Root Port
00:10.0 USB controller: Advanced Micro Devices [AMD] Hudson USB XHCI Controller (rev 03)
00:10.1 USB controller: Advanced Micro Devices [AMD] Hudson USB XHCI Controller (rev 03)
00:11.0 SATA controller: Advanced Micro Devices [AMD] Hudson SATA Controller [AHCI mode] (rev 40)
00:12.0 USB controller: Advanced Micro Devices [AMD] Hudson USB OHCI Controller (rev 11)
00:12.2 USB controller: Advanced Micro Devices [AMD] Hudson USB EHCI Controller (rev 11)
00:13.0 USB controller: Advanced Micro Devices [AMD] Hudson USB OHCI Controller (rev 11)
00:13.2 USB controller: Advanced Micro Devices [AMD] Hudson USB EHCI Controller (rev 11)
00:14.0 SMBus: Advanced Micro Devices [AMD] Hudson SMBus Controller (rev 13)
00:14.1 IDE interface: Advanced Micro Devices [AMD] Hudson IDE Controller
00:14.2 Audio device: Advanced Micro Devices [AMD] Hudson Azalia Controller (rev 01)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] Hudson LPC Bridge (rev 11)
00:14.4 PCI bridge: Advanced Micro Devices [AMD] Hudson PCI Bridge (rev 40)
00:14.5 USB controller: Advanced Micro Devices [AMD] Hudson USB OHCI Controller (rev 11)
00:14.7 SD Host controller: Advanced Micro Devices [AMD] Hudson SD Flash Controller
00:15.0 PCI bridge: Advanced Micro Devices [AMD] Device 43a0
00:15.1 PCI bridge: Advanced Micro Devices [AMD] Device 43a1
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 0 (rev 43)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 6
00:18.6 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 5
00:18.7 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 7
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
02:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)

When I installed 12.10 I discovered a problem that the system does not suspend when the cover is closed.  I fixed that by installing the proprietary fglrx driver but have now found that the fglrx driver only supports a 1600x1600 maximum virtual screen size:  not enough to support attaching a 1080p HD TV as a second display.

How do I resolve this catch 22?

---

### Post by kurt18947 on 2013-01-29
Apologies in advance if I'm being simplistic but does the 'power' applet show suspend when the lid is closed?

---

### Post by jcobban on 2013-01-29
> **kurt18947 said:**
> Apologies in advance if I'm being simplistic but does the 'power' applet show suspend when the lid is closed?
How can I see the power applet if the lid is closed?

As I look at it further it appears that the laptop is actually suspending and then recovering, however because of the fault in the driver Xorg is not displaying everything.  I can tell this because when I close the lid 
[LIST]
[*]The light on the mouse goes out.
[*]The hardware LEDs indicating disk drive, wireless, and power cord go out.
[/LIST]
When I open the lid:
[LIST]
[*]I hear the disk drive spin up.
[*]The hardware LEDs come on.
[*]The light on the mouse comes on.
[/LIST]
However the screen remains black, indicating that the fault in the open driver is preventing Xorg from reactivating the display.

---

### Post by jcobban on 2013-01-29
> **jcobban said:**
> 
...the screen remains black, indicating that the fault in the open driver is preventing Xorg from reactivating the display.
Even restarting Xorg does not bring the display alive.  I have to power off and on to recover.

---

### Post by DracoMaille on 2013-01-29
This is a common issue with Ubuntu Unity ... I had the same problem and found this work-around ... unfortunately it didn't work for me ... might work for your hardware though .... 

[http://ubuntuforums.org/showthread.php?t=1978290](http://ubuntuforums.org/showthread.php?t=1978290)


I could not resolve the issue with waking from suspend in Unity, so I switched to Kubuntu ... no issues so far (and I prefer the KDE interface).  

Just so you know what I am working with:

Toshiba Satellite laptop
AMD A10-4600 quad core w/ integrated Radeon HD 
4Gb DDR3 1600
640Gb HDD
UEFI bios

---

### Post by kurt18947 on 2013-01-30
> **jcobban said:**
> How can I see the power applet if the lid is closed?



As I look at it further it appears that the laptop is actually suspending and then recovering, however because of the fault in the driver Xorg is not displaying everything.  I can tell this because when I close the lid 
[LIST]
[*]The light on the mouse goes out.
[*]The hardware LEDs indicating disk drive, wireless, and power cord go out.
[/LIST]
When I open the lid:
[LIST]
[*]I hear the disk drive spin up.
[*]The hardware LEDs come on.
[*]The light on the mouse comes on.
[/LIST]
However the screen remains black, indicating that the fault in the open driver is preventing Xorg from reactivating the display.

I have a 10 yr. old laptop that does exactly the same thing.  One would think this would have improved over 10 yrs.  The only thought I have - there is a package named something like "AMD Microcode" in the repositories.  Do you have that installed?  I'm not sure what it does but might be worth a try.  I have an AMD desktop w/ Nvidia graphics that would complain on boot up that AMD Microcode was not installed.  I've not had a suspend/resume problem with this desktop though.

---

