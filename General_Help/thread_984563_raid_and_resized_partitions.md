---
title: "raid and resized partitions"
date: 2008-11-16
forum: General Help
---

### Post by cyracks on 2008-11-16
Helo all,

I had perfectly build server but yesterday I decided to resize both disk from raid(1) array so I could gain some more space for swap disks. Since I did it from live cd I assumed everything would be ok, but now when I try to boot the system below error is shown:

```
Check root= bootarg cat /proc/cmdline
        or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/md0 does not exists. Dropping to a shell!
``` I don't have much knowledge about raid managing but somewhere on the forum it was suggested to try rebuilding initramfs, so my steps were:
1) start live cd and then
```
**#mount sda1 and sdb1**
mkdir /sda1
mount /dev/sda1 /sda1
mkdir /sdb1
mount /dev/sdb1 /sdb1
cd /sda1
**# chroot to sda1**
chroot /sda1
**# create backup**
cp -fvpr /boot /boot1
**# create initramfs**
update-initramfs -k 2.6.24-16-server -c -t
**# and then copy /sda1/boot to /sdb1/boot**
```Steps above didn't help and I am still geting the error.
Since I don't want to mess something and loose the data I'am asking you if anybody know what did I break and how to fix it

---

### Post by jorge6422 on 2008-11-17
How did you resize your partiton and how did you creat a RAID 1 ?
Would you show the /etc/fstab ?

---

### Post by cyracks on 2008-11-18
I created raid during the install of the system. Then it took me 2 weeks to configure the system and after creating two virtual machines I decided I need more swap. So I rebooted the system and start ubuntu from live cd, where I resized the partitons with the helo of gparted (both disk have exactly the same partition schema)

/etc/fstab:
```

proc    /proc    proc    defaults    0    0
## /dev/md0
UUID=d8376fa1-3cf0-499e-bc90-1321647ebe4e    /    ext3    relatime,errors=remount-ro,acl    0    1
## /dev/sda2
UUID=3587054c-18a5-486b-a64c-740b06570951    none    swap    sw    0    0
## /dev/sdb2
UUID=a49657c2-0fae-4210-927b-129cd71289e3    none    swap    sw    0    0
/dev/scd0    /media/cdrom0    udf,iso9660    user,noauto,exec,utf8,    0    0

```

---

### Post by psusi on 2008-11-20
I don't think you can use gparted like that.  I think you fouled things up by bypassing the raid and manipulating the underlying disks directly.  Post the output of sudo mdadm -E /dev/sd[ab]1.

---

