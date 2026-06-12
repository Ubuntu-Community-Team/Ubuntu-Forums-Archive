---
title: "grub error 21 when removing secondary disk"
date: 2007-04-26
forum: Hardware &amp; Laptops
---

### Post by jcantara on 2007-04-26
My computer has 4 hard disks, I'll list them as they are now:
hd0 - grub on mbr here, windows 2000 (primary master)
hd1 - gentoo drive, not used and dying (primary slave)
hd2 - file storage drive (secondary master)
hd3 - ubuntu drive (sata first channel)

So, what I'm trying to do is remove hd1 (primary slave), because it's loud as hell and bothers me and I don't use it anyway. I disconnected the drive, powered up the computer and grub gives me error 21. Looking around, I've learned that grub looks for that drive, doesn't find it, and just gives up. I may be wrong about the specifics, but that's how I understand it. I'm not sure if grub has important information on that drive (for some reason), or if it just bails when it can't find that drive instead of gracefully moving on. 

What I want to know is how can I remove the disk successfully? I've tried commenting out everything in /boot/grub/menu.lst and device.map about that disk, but it doesn't seem to matter.

Has anybody run into this before? I'm using Ubuntu 7.04. Is there a way I can reinstall grub and have it ignore that drive as if it weren't there, so when I actually remove it, all is well?

Thanks,
-Jesse

---

### Post by msandersen on 2007-04-28
Is Grub installed on that drive? In which case, re installing Grub on your primary Linux partition before the old drive dies may be a good idea...

---

