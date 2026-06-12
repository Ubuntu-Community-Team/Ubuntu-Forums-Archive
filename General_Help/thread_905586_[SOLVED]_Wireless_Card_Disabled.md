---
title: "[SOLVED] Wireless Card Disabled"
date: 2008-08-30
forum: General Help
---

### Post by scathmandra on 2008-08-30
So I'm running Hardy Heron off my Dell Inspiron 1501 and, having gone through the tedious driver-installing and enabling of the wireless card (Broadcom 43xx, I think) , I only had a bit of time to rejoice. Suddenly, this morning, the little WiFi icon on my laptop shut off, and I wasn't able to access the Internet anymore.

I'm quite sure that the driver's still working; it may just be that I presses something wrong and disabled the wireless card. How do I re-enable it?

---

### Post by EmanresuusernamE on 2008-08-30
Try the hardware switch on your laptop, see if that helps.  Also, make sure it's enabled in your BIOS.

---

### Post by scathmandra on 2008-08-30
I've tried Fn + F2, but it seems to have no effect. How do I make sure it's enabled in my BIOS? Sorry, but I'm a complete newbie at this...

---

### Post by soxs on 2008-08-30
I have the same wifi module.
You should check wether the module b43 gets loaded by defualt.
To check that simply use:
```
cat /etc/modules
```
If the output does not contain any b43, add it:
```
sudo nano /etc/modules
``` and simply add a newline withch says 
```
b43
```
reboot

At least that worked for me, using an HP Compaq nx6325.
You may check any hardware buttons which cut off the current for your wifi device.

EDIT: THIS WILL ONLY WORK IF YOU ALLREADY DWONLOADED THE FIRMWARE WITH UBUNTUS RESTRICTED DRIVER MANAGER!

---

### Post by EmanresuusernamE on 2008-08-30
> **scathmandra said:**
> I've tried Fn + F2, but it seems to have no effect. How do I make sure it's enabled in my BIOS? Sorry, but I'm a complete newbie at this...
There should be a physical switch that you can toggle back and forth to enable and disable the wireless card.  Fn+F2 seems more like an application specific keyboard shortcut designed for Windows.

---

### Post by scathmandra on 2008-08-30
> **EmanresuusernamE said:**
> There should be a physical switch that you can toggle back and forth to enable and disable the wireless card.  Fn+F2 seems more like an application specific keyboard shortcut designed for Windows.
 I can't see one on the Inspiron 1501.

---

### Post by soxs on 2008-08-30
may you plx post the output from:
```
lspci
```
and
```
ifconfig
```

---

### Post by scathmandra on 2008-08-30
lspci:
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]
05:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
08:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
08:01.0 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
08:01.1 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)

ifconfig:
eth0      Link encap:Ethernet  HWaddr 00:1c:23:8d:89:28  
          inet addr:192.168.1.107  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:23ff:fe8d:8928/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1114 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1177 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:985569 (962.4 KB)  TX bytes:256223 (250.2 KB)
          Interrupt:21 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:370 errors:0 dropped:0 overruns:0 frame:0
          TX packets:370 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:18500 (18.0 KB)  TX bytes:18500 (18.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1c:26:7e:b4:e0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-1C-26-7E-B4-E0-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by scathmandra on 2008-08-30
I solved it! I just reinstalled the driver from scratch... that's weird. I have no idea why it didn't show up.

Thank you for taking the time to try to help me! I'm sorry for the trouble.

---

