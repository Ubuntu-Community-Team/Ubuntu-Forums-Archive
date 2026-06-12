---
title: "Wiped HD, installed Ubuntu, can't install wireless driver."
date: 2010-04-16
forum: Hardware
---

### Post by bna2010 on 2010-04-16
Hello, I dont know anything about linux or how to use it.  I barely know what a terminal is.  Im installing it on a small partition just to be able to run the aircrack-ng program.

My ubuntu installation is fresh, my firefox won't connect.  What is the next step to get my wireless working?

Here's my hardware...

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML  Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile  915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML  Express Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6  Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6  Family) PCI Express Port 1 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6  Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6  Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6  Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6  Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6  Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6  Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface  Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6  Family) IDE Controller (rev 03)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX  (rev 02)
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One  54g] 802.11g Wireless LAN Controller (rev 02)

---

### Post by SnickerSnack on 2010-04-16
Not really an answer to your question:

I assume that you also have windows on another partition as your main OS?

I think it would be much better to simply use a virtual machine for when you need to use aircrack-ng.

Here's VirtualBox: [http://www.virtualbox.org/](http://www.virtualbox.org/)

and a site for ubuntu .vdi (virtual disk image = premade vm) torrents: [http://www.mininova.org/search/?search=ubuntu](http://www.mininova.org/search/?search=ubuntu)

---

### Post by PRC09 on 2010-04-16
Hope this helps....


[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

---

### Post by 2hot6ft2 on 2010-04-16
> **bna2010 said:**
> Hello, I dont know anything about linux or how to use it.  I barely know what a terminal is.  Im installing it on a small partition just to be able to run the aircrack-ng program.

There is a aircrack-ng suite for windows. Good luck getting it to work with broadcom chipsets.

[HOWTO: Broadcom 4318 Wireless Cards]("http://ubuntuforums.org/showthread.php?t=197102")

---

