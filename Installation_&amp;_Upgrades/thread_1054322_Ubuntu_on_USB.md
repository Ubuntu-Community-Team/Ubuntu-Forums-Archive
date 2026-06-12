---
title: "Ubuntu on USB"
date: 2009-01-29
forum: Installation &amp; Upgrades
---

### Post by qrees on 2009-01-29
Ok, I was trying to install ubuntu (8.10) no USB drive. Installaton went fine, grub is installed, but when I boot from the usb, there is no grub menu, only grub console. cat /grub/menu.lst prints a lot of garbage (as if the drive was broken or sth), but I can open the files in normal system.

System boots when I use kernel from hardrive. So after the kernel loads the files are readable, but grub somehow can't read them.

/boot/ folder is on separate partition which is FAT-16 (ext on others won't work)

Any ideas? :)
[B]
Solution:[/B]

Ok, problem solved (pity no one answered). Grub have problems with reading FAT partitions (or it seems so), so I had to use different bootloader. Syslinux solved the problem:

**/dev/sdb** - usb drive
**/dev/sdb1** - FAT-16 partition with kernel files (mounted in /boot)
```

syslinux -sf /dev/sdb1
cat /usr/lib/syslinux/mbr.bin > /dev/sdb

```

Now I had to create **syslinux.cfg** file on /dev/sdb1 partition with proper options (read syslinux manual)

and now usb drive will boot properly. Loading kernel and initrd takes some time (about 1m), but after that everything loads quite fast.

---

### Post by qrees on 2009-01-30
to delete... (sorry)

---

