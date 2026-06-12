---
title: "Mount liveCD squashFS filesystem to read-only HDD partition?"
date: 2008-07-18
forum: General Help
---

### Post by MaxIBoy on 2008-07-18
I'd like to mount a rescue distro to a CD-sized partition on my hard drive. This is because I'm planning on fiddling around with my partition map and may need a rescue distro, but I also only have one optical drive, and CDs are way too slow anyway. I'd just select the rescue distro from the bootloader menu (assuming I haven't messed *that* up) if I needed to for any reason, mount my other partitions as read/write, and I'd be good to go. 


Is this possible? How would I do it? I'd like to have at least two other OSs and a swap partition on the hard drive, but I've heard that you can only have three bootable partitions. Is there a way to circumvent that?


Thanks for the help,
-Max

---

### Post by Potatoj316 on 2008-07-18
Are you trying to copy the rescue disk to a partiton on the HD and run from there?

---

### Post by MaxIBoy on 2008-07-18
If that's what I'd have to do, then yes. If I'd need a .iso instead, that's okay too. I'm basically trying to turn a partition into an optical drive with the same CD perpetually in it, accessible using my normal GRUB bootloader. I'm pretty sure the disk image won't know the difference, but I could be wrong. 


This would be done in advance, just in case I need a rescue distro. I'm not planning on waiting until I need one and *then* doing this, if that's what you're asking.

---

