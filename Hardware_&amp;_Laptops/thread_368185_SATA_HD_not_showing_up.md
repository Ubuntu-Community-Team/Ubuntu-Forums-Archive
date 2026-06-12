---
title: "SATA HD not showing up"
date: 2007-02-23
forum: Hardware &amp; Laptops
---

### Post by Roma_emu on 2007-02-23
Hello,

I know that building my own kernel version may not the best thing to do for stability and compatibility (and probably makes being helped here harder), but this is what happened:

After following a ton of guides, tutorials and how-tos to get the latest legacy Nvidia GeForce drivers installed in my computer, I found a guide [(link)](http://www.nvnews.net/vbulletin/showthread.php?t=84298) that told me that I needed a newer kernel version in order to get the latest Nvidia driver to work, and make Beryl work with my old card. However, when I boot with the 2.6.19.2 kernel it told me to compile, my SATA hard disk with Windows disappears. It's not a problem with it being NTFS - there is no /dev/sd* and the drive doesn't appear in the Device Manager. After some searching and thinking, it seems to me that the problem is that there is no sata_via driver in this kernel (don't know if it's missing in this version, or because it's not enabled by default in the kernel compile settings) - modprobe sata_via returns a "module sata_via not found". If I boot with the regular Edgy kernel, it shows up fine. I tried with two different HDs (a Samsung and a Seagate), so that's not the matter either.

Could someone help me with this, tell me what I could do to make it work with this kernel... because I don't want to go back to the regular Edgy kernel, since that would mean using the nv driver and losing Beryl. :(

---

### Post by kidders on 2007-02-23
Hi there,

The first thing to check is whether you selected the SATA driver for compliation. If you compiled in the /proc interface to your kernel configuration, you can find out with something like this. Otherwise, you can just consult the .config you used when compiling the kernel.```
$ gunzip -c /proc/config.gz |grep SATA_VIA
CONFIG_SCSI_SATA_VIA=m
```(The VIA SATA SCSI driver is available as a kernel module on my machine.)

While you're at it, you should check to make sure anything necessary for SATA controllers to work properly is also selected, and that NTFS-related stuff is compiled as well.

---

