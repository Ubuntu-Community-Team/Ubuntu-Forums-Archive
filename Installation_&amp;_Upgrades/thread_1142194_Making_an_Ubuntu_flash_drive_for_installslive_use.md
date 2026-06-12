---
title: "Making an Ubuntu flash drive for installs/live use"
date: 2009-04-28
forum: Installation &amp; Upgrades
---

### Post by Centrist on 2009-04-28
I'm trying to take the Ubuntu 9.04 ISO and extract it to a bootable flash drive. I want to add a few other ISOs after this one, so I'm doing it manually, but I can't seem to get the right config.

Grub is installed in the flash drive's MBR and boots just fine, but Ubuntu takes some time to load and then puts me at a BusyBox prompt. If I look around at the initramfs prompt, I can see casper.log has a lot of errors about not being able to find directories and "unable to find a medium containing a live file system" at the end.

I read through a ton of install guides and launchpad bug reports, but I couldn't find the solution. I saw one bug report for jaunty that said the patch was included in the daily build, but I got the same problem when I tried using it.

My Computer: Asus Eee 1000HE
My Flash drive: 2GB generic with one FAT32 partition
Bootloader: Used my Ubuntu box to install grub to the MBR
ISOs: I downloaded the daily-live 9.04 i386 iso

This is my menu.lst config:

```

default 0
timeout 15

title Ubuntu 9.04 i386 Live
root (hd0,0)
kernel /boot/ubuntu904-i386/casper/vmlinuz file=/boot/ubuntu904-i386/preseed/ubuntu.seed boot=casper quiet splash --
initrd /boot/ubuntu904-i386/casper/initrd.gz

title Ubuntu 9.04 i386 Start or Install
root (hd0,0)
kernel /boot/ubuntu904-i386/casper/vmlinuz file=/boot/ubuntu904-i386/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
initrd /boot/ubuntu904-i386/casper/initrd.gz

title Memtest86+ (from Ubuntu 904 i386 image)
root (hd0,0)
kernel /boot/ubuntu904-i386/install/mt86plus

```

You can see I took the isolinux text.cfg options from the ISO and converted it to use with grub. I have tried many variations on this, and I also tried using configs from some howtos, but no luck! Grub seems to be working just fine, and Memtest boots and runs with no problems.

I think my kernel boot options must be wrong, but I'm not sure how to fix it. Am I correct in thinking I can take the daily-live build, extract to a flash drive, and use grub to boot it?

Would really appreciate some help here.

---

### Post by Centrist on 2009-05-08
Ok, so apparently this is a difficult thing to do... I've gotten a bunch of flash drives and used one for each ISO/image.

---

### Post by simon dew on 2009-05-08
I've successfully installed 9.04 onto a flash card by burning an image of the .iso to a usb memory stick using 'Fedora live usb creator' and then installing the os onto a flash card. It seems to work perfectly apart from a habit of occasionally freezing the screen for a minute or so and sometimes taking a long time to boot up.
simon Asus Eee 7.10

---

