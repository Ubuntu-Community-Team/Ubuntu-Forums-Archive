---
title: "No sound on Toshiba laptop."
date: 2008-05-09
forum: Hardware
---

### Post by Vgonman on 2008-05-09
Hey folks, I just installed U 7.04 Feisty on my my Toshiba Satellite P205-S6337. Everything worked fine while I was running Winblows XP. I got a fresh HDD to install Ubuntu on. Here's the output of the lspci command from a terminal. (I included the whole thing because I figured too much info would be better than not enough). BTW, I do get a volume control in the upper right corner, and when I move the physical volume wheel on the edge of the laptop, another volume bar pops up dead center in the screen, but I still get no noise out of the built in speakers or anything plugged into the headphone jack. Any help would be appreciated.  :)

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
04:00.0 Network controller: Intel Corporation Unknown device 4229 (rev 61)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
06:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
06:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
06:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
06:04.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller

---

### Post by jynyl on 2008-05-09
This seems to be a common problem introduced with Hardy.
[http://ubuntuforums.org/showthread.php?t=782139]("http://ubuntuforums.org/showthread.php?t=782139")

---

### Post by olejorgen on 2008-05-09
Long shot, but it might just be that you've muted the speakers in windows. If I do this on my toshiba I can't get sound when I boot ubuntu.

---

### Post by Vgonman on 2008-05-09
Actually, I installed Feisty Fawn, unless some of the 200 or so updates that my system did right after I installed Feisty took me up to a new version. IDK... I'm great with Windoze, but a complete noob when it comes to Linux.

---

