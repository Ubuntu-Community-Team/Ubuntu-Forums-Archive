---
title: "Motherboard and 64-bit issue"
date: 2014-07-16
forum: Hardware
---

### Post by nut-kicker on 2014-07-16
I have this strange issue that most likely comes from my motherboard. When I install a distro, or liveboot it, everything seems fine until the OS proper starts. What happens then is that the only USB ports that work are the two USB3 in the back, and there is no network connection. At first I thought it was a driver issue. But the thing is, this only happens if I'm in 64-bit. Because when I boot in 32-bit, *everything* works perfectly. But the strangest of all, this happens with *all* distros. Not just a specific distro, or a specific family of distro, *all* 64-bit distros have the same problem, while all 32-bit versions *of these same distros* work perfect. I currently have 13 distros that have 64-bit versions: Netrunner, Mint, Zorin, OpenSuse, Manjaro, Ubuntu, Lxle, Fedora, Centos, Crunchbang, Slackware, Antegros and Debian (I have 24 distros in total but the others are either dual or 32 bit only), and they all do the same thing. And oddly, Windows 8 has no issues (it's where I am right now), while 7 needs drivers, which is why I thought it was a driver issue. But if it was, then both 32 and 64 bit versions would be having the issue. So I don't know what the problem is, but i know it's either drivers or the board itself. And unfortunately, if it is the motherboard, I can't afford to replace it.

So, any help?

The CPU and board are:
AMD FX-8150
Gigabyte 970A-D3 (yeah, I may have made an error to buy this one)

---

### Post by tgalati4 on 2014-07-17
Use the operating system that works with your hardware.  If you can boot into 64-bit, then look through the log files:

```
more /var/log/syslog
```

Take notes and post any USB or network card-related messages.

Try updating the BIOS.

---

### Post by nut-kicker on 2014-07-17
> **tgalati4 said:**
> Use the operating system that works with your hardware.  If you can boot into 64-bit, then look through the log files:

```
more /var/log/syslog
```

Take notes and post any USB or network card-related messages.

Try updating the BIOS.

BIOS updates are mostly only for hardware compatibility like CPUs and RAM and in general are pointless unless there's an issue with the installed one. I still did it in the off chance that it would work, but like I thought it did absolutely nothing.

As for the syslog, well, be my guest:
[https://drive.google.com/file/d/0B8BKU6z-LSaiNThpbkRGaHJ0akE/edit?usp=sharing](https://drive.google.com/file/d/0B8BKU6z-LSaiNThpbkRGaHJ0akE/edit?usp=sharing)   --------32-bit
[https://drive.google.com/file/d/0B8BKU6z-LSaiTE5mdzNSRmE2SlE/edit?usp=sharing](https://drive.google.com/file/d/0B8BKU6z-LSaiTE5mdzNSRmE2SlE/edit?usp=sharing)  --------64-bit

I don't have the time to go through them. The 32 one is from Netrunner 14 32-bit which works and is installed as dual boot, and the 64 one is from Ultimate Edition 4.2. Both are Ubuntu derivatives so they should be close enough to each other to compare.
Now I did have the time to notice this :
usb 2-3: device descriptor read/64, error -110
usb 2-3: new high-speed USB device number 4 using ehci-pci
usb 2-3: device not accepting address 4, error -110
It's repeated quite often with different numbers except the error number always stays, error -110.

---

### Post by QIII on 2014-07-17
Hello!

You may be running in to a problem similar to some of Gigabyte's FXA motherboards.

If you check your BIOS/EFI and find an entry for IOMMU, set it to "Enabled".

When you reboot,

```
sudo gedit /etc/default/grub
```Make sure that the line that starts with 

```
GRUB_CMDLINE_LINUX=
```

contains

```
"iommu=soft"
```

Then 

```
sudo update-grub
```

What this does is takes IOMMU (input/output memory management unit) control away from the motherboard and gives it to the OS.

Reboot and let us know if you have all of your USB ports working properly.


Edit:  I looked around and it seems your board does fall into this category.

---

