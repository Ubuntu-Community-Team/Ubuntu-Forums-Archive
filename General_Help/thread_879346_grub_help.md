---
title: "grub help"
date: 2008-08-03
forum: General Help
---

### Post by LostAngel on 2008-08-03
Hello, my original setup was a 200GB ubuntu partition (SD2), and a 15GB windows partition (SD1). I resized the ubuntu partition to 150GB, and created a new partition with that freespace (SD4).  I then copied SD1 to SD4 in gparted.  How can I set GRUB to boot into the SD4 for windows, instead of the original windows partition?

---

### Post by spiderbatdad on 2008-08-03
i think this can be done by editing your /boot/grub/menu.lst in the windows section.
can you post the file here, along with ```
sudo fdisk -l
```

---

### Post by LostAngel on 2008-08-03
default 0
timeout 10

title Ubuntu 8.04.1, kernel 2.6.24-19-generic
root (hd0,1)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=6845cb55-d6bc-4ab8-b54c-cc7eab59ede3 ro quiet splash
initrd /boot/initrd.img-2.6.24-19-generic
quiet

title Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root (hd0,1)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=6845cb55-d6bc-4ab8-b54c-cc7eab59ede3 ro single
initrd /boot/initrd.img-2.6.24-19-generic

title Ubuntu 8.04.1, kernel 2.6.24-18-generic
root (hd0,1)
kernel /boot/vmlinuz-2.6.24-18-generic root=UUID=6845cb55-d6bc-4ab8-b54c-cc7eab59ede3 ro quiet splash
initrd /boot/initrd.img-2.6.24-18-generic
quiet

title Ubuntu 8.04.1, kernel 2.6.24-18-generic (recovery mode)
root (hd0,1)
kernel /boot/vmlinuz-2.6.24-18-generic root=UUID=6845cb55-d6bc-4ab8-b54c-cc7eab59ede3 ro single
initrd /boot/initrd.img-2.6.24-18-generic

title Ubuntu 8.04.1, kernel 2.6.24-16-386
root (hd0,1)
kernel /boot/vmlinuz-2.6.24-16-386 root=UUID=6845cb55-d6bc-4ab8-b54c-cc7eab59ede3 ro quiet splash
initrd /boot/initrd.img-2.6.24-16-386
quiet

title Ubuntu 8.04.1, kernel 2.6.24-16-386 (recovery mode)
root (hd0,1)
kernel /boot/vmlinuz-2.6.24-16-386 root=UUID=6845cb55-d6bc-4ab8-b54c-cc7eab59ede3 ro single
initrd /boot/initrd.img-2.6.24-16-386

title Ubuntu 8.04.1, kernel 2.6.22-14-generic
root (hd0,1)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=6845cb55-d6bc-4ab8-b54c-cc7eab59ede3 ro quiet splash
initrd /boot/initrd.img-2.6.22-14-generic
quiet

title Ubuntu 8.04.1, kernel 2.6.22-14-generic (recovery mode)
root (hd0,1)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=6845cb55-d6bc-4ab8-b54c-cc7eab59ede3 ro single
initrd /boot/initrd.img-2.6.22-14-generic

title Ubuntu 8.04.1, memtest86+
root (hd0,1)
kernel /boot/memtest86+.bin
quiet

title Other operating systems:
root 

title Microsoft Windows XP Professional
root (hd0,0)
chainloader +1
savedefault
makeactive

---

### Post by spiderbatdad on 2008-08-03
title Microsoft Windows XP Professional
root (hd0,**4**)
chainloader +1
savedefault
makeactive 

Is what I think you want.

---

### Post by spiderbatdad on 2008-08-03
ah actually it might be (hd0,3) as you can see, counting begins at 0. Where your previous setup had windows on the first hd and first partition, you had (hd0,0) and for ubuntu on sda2...you had (hd0,1)

---

### Post by LostAngel on 2008-08-03
Tried 0,3 and it just loads my original windows partition...0,4 does not work.

---

### Post by spiderbatdad on 2008-08-03
> **LostAngel said:**
> Tried 0,3 and it just loads my original windows partition...0,4 does not work.

That sound like what you wanted?
You said you copied sda1 to sda4 and you were trying to get it to boot...or did I miss something?

---

### Post by LostAngel on 2008-08-03
when it loads 0,3...it is showing my C:\ drive as being the original size it was...shouldn't it show what the new partition is?

---

### Post by spiderbatdad on 2008-08-04
I'm not sure this is possible with gparted. If the windows partition was before the ext3 partition, I think gparted can only expand the end of ext3 partitions. Hopefully you have backed up your data on external media before doing anything else with partitioning. Did you try the gparted live cd?

---

### Post by LostAngel on 2008-08-04
Yes, the NTFS system is before my ext3 partition.  Would I be able to do the following?  Reduce my EXT3 partition by 50GB...make that 50GB an NTFS system...reinstall windows on that partition...copy all my files from my original NTFS partition...then delete the original and resize my EXT3 partition to 'consume' the original partition that was NTFS?

---

