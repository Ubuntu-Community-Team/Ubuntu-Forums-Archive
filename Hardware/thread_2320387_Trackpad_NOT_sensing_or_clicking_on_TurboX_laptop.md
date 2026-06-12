---
title: "Trackpad NOT sensing or clicking on TurboX laptop"
date: 2016-04-13
forum: Hardware
---

### Post by turbotoff on 2016-04-13
Hi Guys, 


I am new to the Linux world, though i have successfully installed Lubuntu on my girlfriend's old laptop which was sold under the brand Turbo-X / Model: X11A. I don't recall what version of Windows it was running before (Vista, i think), but i could not reinstall Windows after it got a virus, and decided to format the whole thing and install Lubuntu which appears to have gone through fine. I can get on the internet through ethernet and can do upgrades etc. My issue at the moment is the **Trackpad** - (I also have a wireless problem but i have posted a separately for that.) 


I am able to use an old logitech wireless mouse with usb transmitter, but the trackpad _does not sense touch and the clicker does not respond_ when i press on the clicker button.


I am very proficient with Macs, I am semi-proficient with Windows, but I am completely noob with Linux.


Please can someone guide me on getting this working. Am hoping it's kinda simple to fix.


I believe i'm on Lubu v15.10


Thanks!

---

### Post by turbotoff on 2016-04-13
Running lspci through Terminal gives me this output:

```
pinky@pinky-laptop:~$ lspci00:00.0 Host bridge: Intel Corporation Mobile 945GSE Express Memory Controller Hub (rev 03)00:02.0 VGA compatible controller: Intel Corporation Mobile 945GSE Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 3 (rev 02)
00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [IDE mode] (rev 02)
00:1f.3 SMBus: Intel Corporation NM10/ICH7 Family SMBus Controller (rev 02)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 03)
pinky@pinky-laptop:~$
```

---

