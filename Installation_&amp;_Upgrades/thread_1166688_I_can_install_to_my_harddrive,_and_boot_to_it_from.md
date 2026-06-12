---
title: "I can install to my harddrive, and boot to it from CD, but not without the CD..."
date: 2009-05-22
forum: Installation &amp; Upgrades
---

### Post by ButtDyno on 2009-05-22
So I'm installing 8.0.4 (I already had the ISO) on a spare laptop.

It stopped booting into Windows a while ago and we assumed it was the hard drive. So I bought another one, but it doesn't fit. I decided to try installing Ubuntu onto the old disk anyway. I boot off the CD, it sees my hard drive, it wipes it out and copies everything over. It tells me to eject the CD, I do, and when it reboots... it says no bootable device.

Crap!

So I boot off the CD, figuring oh well, at least I can boot into the CD environment. I decide to try the "boot from local disk" option on a whim. Much to my surprise, it works. Eh? 

Anyone know what would cause this to happen? The hard drive works fine, EXCEPT when I'm trying to boot it up. I've never seen anything like this.

thanks,
john

p.s. not my first cup of ubuntu... been using it for a year or so, and been using Linux since 1997.

---

### Post by x33a on 2009-05-22
maybe it's a grub error.

try reinstalling grub.

---

### Post by pastalavista on 2009-05-22
Once, when I changed my BIOS to boot first from USB, I forgot to tell it when to boot from ATA/IDE.
got that same message

---

### Post by Sef on 2009-05-22
> maybe it's a grub error.

try reinstalling grub.

Check out [Super GRUB Disk]("http://supergrubdisk.org") - the easy way to reinstall GRUB.

---

### Post by ButtDyno on 2009-05-22
> **x33a said:**
> maybe it's a grub error.

try reinstalling grub.Did that, just to be sure.

> **pastalavista said:**
> Once, when I changed my BIOS to boot first from USB, I forgot to tell it when to boot from ATA/IDE.
got that same messageSo... in the BIOS list of things to boot, apparently things aren't "on the list" unless they are highlighted. I thought the Internal HDD option was just lower on the list, but it turns out it was disabled. Good catch! 

It boots off the disk now. Awesome! Thank you!

john

---

