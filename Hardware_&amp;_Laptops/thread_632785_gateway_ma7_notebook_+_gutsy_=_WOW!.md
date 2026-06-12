---
title: "gateway ma7 notebook + gutsy = WOW!"
date: 2007-12-05
forum: Hardware &amp; Laptops
---

### Post by shinepuppy on 2007-12-05
Hi gang,
I just installed Gutsy on this Gateway MA7 notebook and it is the first time an Ubuntu install has worked out of the box for me with 0 *farting-around-with* :) Video, compiz, wireless, sound, nic, speakers, track pad, external monitor.... everything! I nearly fell out of my chair when I clicked on the NetworkManager icon and a list of wireless APs populated the drop down box WITHOUT an hour of jacking around with madwifi or ndiswrapper :) Kudos! Here is the output from lspci for anyone looking for great hardware compatibility:

```
jemanuel@moo:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
04:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
04:09.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
04:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
```

---

### Post by Maxei on 2008-01-18
Hey shinepuppy: 
Lucky you! I have installed Debian Etch on my Gateway MT6840 Notebook. The installation went smooth and I got basically all I needed working (the wireless connection was not tested though). However, the sound became my nightmare because after updating, no more sound can be heard.  I notice your laptop has the same audio device like mine (Audio device: Intel Corporation 82801G (ICH7 Family). I wonder If I should install the Gutsy version. Can you tell which kernel version are you using please?  My kernel is 2.6.18-4. I will try to correct the sound problem in Debian first. **I also have a question**: Have you updated your kernel or installed the updates for your system? If so, does still sound work for you? Thanks for the info.

---

