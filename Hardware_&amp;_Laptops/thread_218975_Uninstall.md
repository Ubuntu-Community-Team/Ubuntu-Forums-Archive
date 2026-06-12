---
title: "Uninstall"
date: 2006-07-19
forum: Hardware &amp; Laptops
---

### Post by mzracer360 on 2006-07-19
I recently install Ubuntu on my Toshiba laptop.  I've been playing around with it for a few months now, but I don't enjoy it as much as I thought I would.  I also have Windows XP Home Edition on my laptop.  I am wanting to know how to remove Ubuntu and GRUB completely.  I know about the method of "fixmbr" but I don't have a Windows CD, all I have is the Toshiba Recovery CD which I've already tried using.  And I don't have a floppy drive to use a bootable floppy with either.  Is there any other way of uninstalling Ubuntu and restoring my MBR?

---

### Post by Jagot on 2006-07-19
To restore MBR you can use a FreeDOS boot disk (it's a CD image file, not a floppy) from here:

[http://www.freedos.org/](http://www.freedos.org/)

Boot with the disk and navigate to the command prompt, then type:

```
fdisk /mbr
```

You can use the Ubuntu Live CD of GParted Live CD or something then to overwrite the partition on which Ubuntu was installed with an NTFS or FAT32 partition or whatever you want.

---

