---
title: "Wifi and webcam problems, dual boot"
date: 2013-12-20
forum: Hardware
---

### Post by z-simon-0 on 2013-12-20
Right, I would like some explanations and some reassurance that someone somewhere is aware of the problem AND IS going to do something about it. I made the terrible mistake of installing ubuntu on another laptop after installing it on my old one which permanently removed my built in wifi (on a HP NC4200). So having not learnt I have installed it on my new laptop, guess what ? yes My wifi adapter while all drivered up will not work even in windows where as it did before instaklling ubuntu, now I find that oh what a flaming coincidence, the webcam that I know worked before on windows BEFORE installing ubuntu no no longer exists either......

Please can someone expain WTF is going on and hopefully tell me how to get my hardware back ! I bought a new laptop so that along with increased computing power I would have up to date integrated devices, but I find that thanks to ubuntu I now have a useless brick as to use what I would have had built into the laptop I will now have to use a usb hub with a USB wifi dongle and also plug in my very old and crappy webcam because I'll be damned that I'm buying another one after paying for it in my laptop.

---

### Post by tgalati4 on 2013-12-20
Well, you have to take at least some responsibility.  You bought a laptop.  It had an operating system on it.  Presumably everything worked.  Then you installed Ubuntu.  Some things are broken.  Have you search for some solutions?

According to HP it is certified for Novel/Suse Linux:  [http://h71028.www7.hp.com/enterprise/cache/312891-0-0-0-121.html](http://h71028.www7.hp.com/enterprise/cache/312891-0-0-0-121.html)

You will have to do some research.

Open a terminal and post the output of:

```
lsusb
lspci
```

---

### Post by z-simon-0 on 2013-12-20
The laptop was blank when bought although I installed windows first hence i know that all hardware worked until I installed ubuntu. This is not about compatibility of hardware with ubuntu, this is about ubuntu physically disabling hardware. I am aware and accept that ubuntu will not be compatible with all hardware but I can't see the point in ubuntu rendering this hardware unusable full stop even by windows.

---

### Post by tgalati4 on 2013-12-20
So the above commands do not show your web camera or your wifi card?  If you don't respond to a support request, then this thread becomes a rant and will be closed.

---

### Post by oldos2er on 2013-12-20
Please provide the information tgalati4 asked for; we need specific hardware info before anyone can advise you.

---

### Post by z-simon-0 on 2013-12-21
Thankyou for your responses, please see below.

simon@simon-ubuntu-laptop:~$ lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 10c4:ea60 Cygnal Integrated Products, Inc. CP210x Composite Device (This is a bit coin miner)
Bus 003 Device 003: ID 046d:c05b Logitech, Inc. M-U0004 810-001317 [B110 Optical USB Mouse]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0846:9018 NetGear, Inc. WNDA3200 802.11abgn Wireless Adapter [Atheros AR7010+AR9280] (This is the USB wifi dongle I am using instead of the non functional built in)
simon@simon-ubuntu-laptop:~$ 

simon@simon-ubuntu-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.2 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 3 (rev c4)
00:1c.3 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 4 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation 7 Series Chipset Family LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8723AE PCIe Wireless Network Adapter (this would be the one that does not work)
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5289 (rev 01)
03:00.2 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0a)
simon@simon-ubuntu-laptop:~$

Hm interesting new title, this has nothing to do with a dual boot situation, the fact that I have windows on it as well and that the same hardware worked under windows and has now vanished merely points to the fact that it is ubuntu that has done the damage and even if I was flying solo with ubuntu my hardware would still not work but I'd have no backup as to the fact that it once did work. I would also say that this is a problem that could affect any hardware in principle.

---

### Post by mörgæs on 2013-12-21
I changed the thread title as the original one didn't provide much information.

---

### Post by tgalati4 on 2013-12-26
Let's work on the wireless card first:

Post:

```
lsmod
```

Try some of the suggestions in this post:

[http://ubuntuforums.org/showthread.php?t=2194870&highlight=RTL8723AE](http://ubuntuforums.org/showthread.php?t=2194870&highlight=RTL8723AE)

---

### Post by z-simon-0 on 2013-12-27
Thanks for the reply, I've managed to get the wireless working. I tried the windows trouble shooter for wireless and it said it was disabled. I needed to turn it "back on" (not that it had been turned off) with the hotkeys so that is working now in windows (I'll assume that going back into ubuntu may turn it off again). The wifi was visible in the windows hardware manager.

The webcam though has become totally invisible, the driver in windows is installed but it's not in the hardware manager unless it's the non descript HID device, naturally ubuntu knows nothing of the webcan although again there was a non descript device in the list so maybe that is it ?

---

