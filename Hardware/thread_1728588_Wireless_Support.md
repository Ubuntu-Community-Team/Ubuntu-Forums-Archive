---
title: "Wireless Support"
date: 2011-04-13
forum: Hardware
---

### Post by qrrbrrbbl on 2011-04-13
I am currently running Joli OS 1.2 on my netbook (HP Mini 110-3018ca, seen [here]("http://h10025.www1.hp.com/ewfrf/wc/product?cc=us&lc=en&dlc=en&product=4229981")), and have started to run into problems with it. It has been eating up hundreds of megabytes of space all on its own, and I find it too web-based. I installed using their express installer, which is similar to Wubi. 

I've decided to try Ubuntu on my netbook, but I'm not sure if I'll run into problems with my netbook's wireless card. Is there a terminal command that can determine the card I have so I can figure out if it will work? The same commands should work from Ubuntu.

This is the output of lspci

Me@jolicloud:~$ lspci
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 04)
01:00.1 Class ff00: Realtek Semiconductor Co., Ltd. Device 5288 (rev 01)
02:00.0 Network controller: RaLink RT3090 Wireless 802.11n 1T/1R PCIe

If that's not the command I needed, I'll be happy to try the correct one. I also plan on testing 10.10 now, and installing 11.04 when the final version is released, if that helps.

---

### Post by K_45 on 2011-04-13
Install Ubuntu to a USB here:

[http://www.ubuntu.com/netbook/get-ubuntu/download](http://www.ubuntu.com/netbook/get-ubuntu/download)

and boot from it, and see if wireless works.

---

### Post by qrrbrrbbl on 2011-04-13
Thanks, but are you able to tell me what my wireless card is? Is it that RaLink RT3090 at the bottom there? I'd just like to Google these things before I potentially waste bandwidth downloading it. I'm still kind of new to Linux.

---

### Post by K_45 on 2011-04-13
Yes, that is the wireless chipset.

---

### Post by qrrbrrbbl on 2011-04-13
Okay, it appears that it works under the 32-bit version of 10.10, but not the 64-bit. I imagine the netbook edition is 32-bit, though. But it also appears that it worked under 9.10, but not 10.04. Hopefully, it doesn't break on 11.04.

Thank you.

---

### Post by K_45 on 2011-04-13
32-bit is fine. Installing 64-bit on a netbook is rather pointless seeing as you have limited memory and CPU support.

---

