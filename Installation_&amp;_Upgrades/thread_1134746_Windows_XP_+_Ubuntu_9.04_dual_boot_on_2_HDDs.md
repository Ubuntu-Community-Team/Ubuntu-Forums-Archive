---
title: "Windows XP + Ubuntu 9.04 dual boot on 2 HDDs"
date: 2009-04-23
forum: Installation &amp; Upgrades
---

### Post by BSK on 2009-04-23
Hi,

here's my hardware setup.

320 gigs on SATA0 so /dev/sda with Windows XP
200 gigs on SATA1 so /dev/sdb with Ubuntu

I installed Windows XP first then installed Ubuntu on the other disk.  Grub is installed on /dev/sdb MBR so I configured my BIOS to boot my second HDD first.

Grub loads fine and I can boot Ubuntu without problems but I cannot boot Windows XP from Grub.  I can only boot Windows XP by modifying my BIOS boot sequence.

Right now I have this in /boot/grub/menu.lst for Windows
```
title Windows XP
root (hd0,0)
savedefault
makeactive
chainloader +1
```

/boot/grub/device.map contains
```
(hd0) /dev/sda
(hd1) /dev/sdb
```

Can anyone tell me what I am doing wrong ?

Thanks

---

### Post by BSK on 2009-04-24
I forgot to mention that I run ;

Windows is XP Pro SP3 32bit

and

Ubuntu 9.04 AMD64

Thanks

---

### Post by Mze on 2009-04-24
Try this:

```
title WinXP
rootnoverify (hd0,0)
makeactive
chainloader +1
```

If that doesn't help, post results of ```
sudo fdisk -l
```

---

### Post by BSK on 2009-04-25
didn't work.

Here's fdisk -l output :
```

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x810e810e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38913   312568641    7  HPFS/NTFS

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x05eb230e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       23330   187398193+  83  Linux
/dev/sdb2           23331       24321     7960207+   5  Extended
/dev/sdb5           23331       24321     7960176   82  Linux swap / Solaris
```

---

### Post by Mze on 2009-04-25
didn't work?

what error message are you getting?

Have checked the [grub manual]("http://www.linuxselfhelp.com/gnu/grub/html_chapter/grub_12.html#SEC64") and this [tutorial]("http://en.opensuse.org/Dual_boot_on_2_drives") and nothing else comes to mind.

You could also consider [EasyBCD]("http://neosmart.net/dl.php?id=1") as a last resort.

---

### Post by BSK on 2009-04-26
no error message, it just seems to load for a second then I get back to the grub menu.

---

### Post by Mark Phelps on 2009-04-26
You're booting from your Ubuntu drive, right?  That makes it the first drive that Grub sees -- hd0.

Try the following:
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1,0)
savedefault
chainloader +1

---

### Post by BSK on 2009-04-27
nice, that worked!

Yes I do boot from the "second" Ubuntu hdd so my Windows hdd is untouched by the linux installation, I like it that way.

Thanks a lot!:)

---

