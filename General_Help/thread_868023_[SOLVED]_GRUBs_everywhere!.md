---
title: "[SOLVED] GRUBs everywhere!"
date: 2008-07-23
forum: General Help
---

### Post by skutter2k on 2008-07-23
I have the following setup:

/dev/sda1 (NTFS)
/dev/sda2 (extended)
    /dev/sda5 (ext3)
    /dev/sda6 (linux-swap)

/dev/sdb1 (linux-swap)
/dev/sdb2 (ntfs)
/dev/sdb3 (extended)
    /dev/sdb5 (ext3)

I am trying to shift everything linux related from sda to sdb.

I have successfully rsync'd everything from /dev/sda5 to /dev/sdb5 but no matter how much I play with grub I can't seem to get it to boot from anything other than /dev/sda5.

Any advice on using grub with the configuration above would be great as despite reading a lot of documentation and thinking I have nailed it, it still doesn't work, lol!

Thanks

---

### Post by northern lights on 2008-07-23
in GRUB syntax sdb5 is hd(1,4)

I.e. your Ubuntu entry should look something like: ```
title		Ubuntu 8.04.1, kernel 2.6.XX-XX-generic
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.XX-XX-generic root=UUID=70113eaf-6b2d-404b-b23e-b08604831b8d ro quiet splash
initrd		/boot/initrd.img-2.6.XX-XX-generic
quiet
```

where XX  your kernel version, most likely "24-19". Alter accordingly if it's not Hardy.

---

### Post by mikewhatever on 2008-07-23
You'd also need to edit your fstab according to the new setup.

---

### Post by skutter2k on 2008-07-23
Aha, that was my next question... I have sorted grub now, I think, but my fstab shows this:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=0016f873-4866-4896-87a5-c93ab5e8e498 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=32def50e-664b-4f12-8323-97e39f882c5d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

I'm guessing it is the line after /dev/sda5 that I need to change but I can't figure out what to exactly!  Sorry to be such a noob, to be honest I'm impressed I got this far however I am already looking forward to getting rid of those NTFS partitions in the near future :)

---

### Post by skutter2k on 2008-07-23
Ok, figured out that I need the UUID (doh!), so looked that up and changed the fstab accordingly but no change when I started up so I'm guessing that means that grub is not looking at hd1,4 afterall?

---

### Post by skutter2k on 2008-07-23
Hurrah!  After wittering to myself I noticed the UUID in the GRUB setting too. Changed that as well as the fstab and all seems well!

Thanks both for pointing me in the right direct. Now I know the whole process it's actually very simple and so far ahead of all things MS based... I love it.

Cheers

---

