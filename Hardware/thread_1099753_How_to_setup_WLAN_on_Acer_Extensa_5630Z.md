---
title: "How to setup WLAN on Acer Extensa 5630Z?"
date: 2009-03-18
forum: Hardware
---

### Post by tretti on 2009-03-18
Hey there!

I've just bought myself a new **Acer Extensa 5630Z**. It comes with Linpus Linux preinstalled, but since this system isn't a "real" operating system I've installed Ubuntu (been a Ubuntu desktop user since 2 years now).

Everything is working fine, but there's one problem: Ubuntu doesn't even seem to recognize that my laptop has got a WLAN chip bulit in. So my question is: How can I find out which chip is build into my system, and how can I get in running?

Thank you very much for your help in advance! :)

---

### Post by tretti on 2009-03-18
Okay, i found out how to check my hardware:


```
patrick@patrick-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5764M Gigabit Ethernet PCIe (rev 10)
03:00.0 Network controller: RaLink Device 0781
0d:06.0 CardBus bridge: O2 Micro, Inc. Cardbus bridge (rev 01)
0d:06.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02)
0d:06.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 03)
patrick@patrick-laptop:~$ 

```

So, I guess that this is my WLAN chip, isn't it?

```
03:00.0 Network controller: RaLink Device 0781
```

---

### Post by tretti on 2009-03-19
Well, even though nobody was able to help me out, my question has been solved in another German Linux forum ([http://www.ubuntu-forum.de/post/255106/wie-wlan-auf-meinem-acer-extensa-5630z-einrichten.html]("http://www.ubuntu-forum.de/post/255106/wie-wlan-auf-meinem-acer-extensa-5630z-einrichten.html")) - There's a guide on how to install the driver for the chip here: [http://www.ubuntu-forum.de/index.php?page=ExternalLink&url=https%3A%2F%2Fanswers.launchpad.net%2Fubuntu%2F%2Bquestion%2F64171]("http://www.ubuntu-forum.de/index.php?page=ExternalLink&url=https%3A%2F%2Fanswers.launchpad.net%2Fubuntu%2F%2Bquestion%2F64171")

---

### Post by dmy49 on 2009-04-02
Thank you! 
I was having same problem with Wireless on my LG R410 (LG XNOTE), and  your post helped. Looks like RT2860 is not supported out of box. 

I downloaded the driver [rt2860-source_1.8.0.0-3_all.deb]("http://packages.debian.org/sid/all/rt2860-source/download"), installed it, and it worked. Also I added rt2860sta to /etc/modules to load the module automatically on each reboot.

Detailed instructions are on the above links or [https://bugs.launchpad.net/linux/+bug/210725/comments/152](https://bugs.launchpad.net/linux/+bug/210725/comments/152).

dm

---

