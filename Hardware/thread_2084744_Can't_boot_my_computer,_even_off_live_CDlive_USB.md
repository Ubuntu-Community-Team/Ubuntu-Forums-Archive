---
title: "Can't boot my computer, even off live CD/live USB"
date: 2012-11-16
forum: Hardware
---

### Post by blackbird34 on 2012-11-16
Hi
Title says it all. 
I have tried booting off various Live USBs and SuperGrub2Disk and from my three linux installs on the hard drive, none of them will load. 
When I boot from my hard drive, i get a "kernel panic - not syncing: out of memory and no killable processes" message.
When I boot from LiveUSB (using Ubuntu 12.04) I get some form of grub error.
Could someone help please?

---

### Post by Polydorus on 2012-11-16
Do you have a live CD/DVD you can try?

---

### Post by blackbird34 on 2012-11-16
Tried, it gives me a grub error. I'm burning a new iso to usb to have another go...

---

### Post by offgridguy on 2012-11-16
> **blackbird34 said:**
> Tried, it gives me a grub error. I'm burning a new iso to usb to have another go...

Have you tried here.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

You can burn a live boot repair CD from this site, really handy to have for times like
these.

---

### Post by blackbird34 on 2012-11-21
1) On a side note, is booting from CD any different to booting from USB? 

I've tried using my computer's WIndows Recovery Disc to reinstall Windows, it just shows the "Windows is loading files" progress bar, then hangs on the splash screen where the Windows logo usually glows a bit (before giving you a login screen etc.).

I've also tried booting from the grub command line as described here: [http://tuxers.com/main/instigating-a-manual-boot-from-the-grub-prompt/](http://tuxers.com/main/instigating-a-manual-boot-from-the-grub-prompt/)

>  [FROM THE SITE, under "Booting Ubuntu installed on disk partitions"]

set root=(hd0,msdos1) &#8211; this specifies the partition from which to load the images.
linux /vmlinuz ro root=/dev/sda2 &#8211; Load this Linux kernel, with arguments
initrd /initrd.img &#8211; load this Initial RAM disk
boot &#8211; Fire it up.
 
- with the commands adapted for my partitioning scheme.

I got the same "Kernel panic [etc.]" message - thus meaning that my computer won't boot at all, so I can't use a Live System.

Is there any way to get at the files or at a BASH prompt through the GRUB command prompt? (EDIT: no, I asked on IRC)

Further EDIT: I gave up on this machine, I think i've really bricked it, I'm going to get it picked up and repaired as its under warranty.

---

