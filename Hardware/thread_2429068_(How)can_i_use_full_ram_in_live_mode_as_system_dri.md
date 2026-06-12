---
title: "(How)can i use full ram in live mode as system drive?"
date: 2019-10-13
forum: Hardware
---

### Post by jasper99 on 2019-10-13
My PC have 32 GB of ram, the system drive in ubuntu is only 16 GB in live mode. can i use the full 32GB of ram as system drive? Or for example 28GB as system drive and 4 GB as RAM (don't know if any of the RAM is as RAM using)

---

### Post by The Cog on 2019-10-13
My advice is don't bother. I say this because 
* You have to have a hard system drive to store the system when powered down, so any RAM based system drive you have will just be a cached copy of the hard drive, and 
* Linux uses all the unused RAM for disk drive caching anyway, so with 32G RAM your system drive (the parts you use, at least) will already be cached in RAM. No special action required.

Incidentally, there is also /dev/shm which is a filesystem that is only stored in RAM if you want to put temporary stuff there - its contents get lost upon reboot of course.

---

### Post by oldfred on 2019-10-13
If using live system, you can edit grub (if UEFI) or syslinux configuration file (if BIOS) to add toram boot parameter. That puts the entire ISO into RAM from slower flash drive. You can only do that if on flash drive, as DVD is not writeable.

---

