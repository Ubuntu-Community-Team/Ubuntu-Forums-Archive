---
title: "At my wits end."
date: 2009-01-01
forum: Installation &amp; Upgrades
---

### Post by seks2 on 2009-01-01
I have spent almost an entire day trying to get this sorted. I bought a new hard drive and simply wanted to do a fresh install of Intrepid on it. The drive was recognized fine, but I have had no luck creating proper installation media. At least ten cd-r disks have been coastered with different disk burner/burning program/write speed combinations. I tested them on different computers, with the same result upon choosing a menu item every time: I/O error, reboot.

I checked the md5 of the iso and cross referenced it to the official one. Exactly the same. I re-downloaded a couple of times in the hopes that it would be something different to no avail. I tried the alternate CD, only to be given errors while copying files, even after it passed the validity check (tested the same on two computers, gave me i/o errors but then said the disk was fine). Unetbootin and wubi won't let me install to a different drive. USB intrepid works like a charm, but my motherboard doesn't support booting from it. My hardy cd also works, but that's not the point of the latest fresh install.

I can't access my ubuntu partition since installing, only windows. Ubuntu drops me to a busybox because it can't find the kernel or something (tried editing the uuid with /dev/hda, /dev/sda, /dev/sda1 and /dev/sda2). I plugged the new HDD into sata 1 and the old into sata 2 but set sata 2 to boot (for now).

Can anyone recommend ANYTHING please? Am I doing something wrong? Can I boot a usb from a command line such as busybox? Can I use unetbootin within an older livecd to install a newer version of ubuntu? Does anyone at least know how to get back into my orignal install? Help would be greatly appreciated :(

EDIT: Never got a CD to work. Used grub to boot the usb installer.

---

