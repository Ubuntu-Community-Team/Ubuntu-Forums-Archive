---
title: "Errounsly made my Windows filesystem vfat"
date: 2009-02-25
forum: Installation &amp; Upgrades
---

### Post by BioGeek on 2009-02-25
Hi, I have errounsly made my Windows filesystem vfat.

This is what happend: I have a Windows laptop that I want to convert to a dual-boot system. To test things out, I was playing around booted from an Ubuntu 9.04 alpha Live CD. I also recently acquired an Openmoko Freerunner and wanted to put hackable:1 as operating system on it's micro-SD card.

So I had the micro-SD card connected to the laptop via an USB card reader. Ubuntu had mounted the card reader to device /dev/sdc1. Following [this tutorial ]("http://www.hackable1.org/wiki/Documentation")I unmounted the device, started fdisk, created an 8M partition of type vfat on the micro-SD card and a second partition of type ext2.

Then I needed to format the SD card and, blindingly following the tutorial, I typed

```
# mkfs.vfat /dev/sda1
```

However, my SD card was on /dev/sdc1, /dev/sda1 is my Windows hard drive. A second too late I realised my mistake and exited Ubuntu, removed the Live Cd and rebooted.

The laptop didn't even want to boot up and displayed the message: "This is not a bootable device please insert a floppy disk"

Fortunately I have a recent backup of all my personal files on my hard drive, but not of the programs themselves. What is the best way to acces my hard drive again? I've downloaded the rescue remix.

thanks in advance!

---

