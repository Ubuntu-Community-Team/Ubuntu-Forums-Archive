---
title: "Lost sdb1 by &quot;fsck /dev/sdb&quot;"
date: 2008-02-12
forum: Hardware &amp; Laptops
---

### Post by giorgione on 2008-02-12
Hi there,

I have two internal Hard Disk Drives in my PC and while booting my machine, fsck tried to check my 2. hard drive (sdb) and showed some errors. I did not exactly understand what they meant so after my machine finished booting I unmounted the drive and did a

```
sudo fsck -y /dev/sdb
```

This also gave me some errors. After that I did a

```
sudo fsck.ext3 -p /dev/sdb
```

to repair the problems. This gave me an error including:

```
UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY
```

so I did that again:

```
sudo fsck /dev/sdb
```

This finished without error, I was happy and did a reboot. But now my /dev/sdb1/ was gone and I was not able to mount this partition.

Does someone know how to restore the sdb1? 

Thank you very very much. There is enough data on that drive that I would really prefer not to lose.

---

### Post by mrsteveman1 on 2008-02-12
First boot an existing linux system (ubuntu livecd perhaps)

Get fdisk to read the partition table from the disk 

```
sudo fdisk -l /dev/sdb
```

If there isnt any visible partition table you may have to use gpart (not gparted) to recover the partition table. From there you would then get your partitions back but they may have errors, though you should be able to then fsck the actual partition and recover most of your data.

---

### Post by giorgione on 2008-02-12
Thank you. The partition table on sdb is gone as you thought. gpart is running righ now.... but I was asking myself how did I screw up?
Will ```
 fsck /dev/sdb
``` always erase the partition table on sdb? I find this strange ...?

---

### Post by mrsteveman1 on 2008-02-12
Fsck technically should check whatever you point it at for a known filesystem and then decide which version of fsck to use. If it doesn't even find a volume (like ext3) it SHOULD just exit.

In fact it shouldn't actually write anything unless it finds a valid filesystem in the first place, but i can't be sure of this, it could be that any number of things overwrote the partition table.

If the partitions and their boundaries have not been screwed with gpart should be able to find the partitions and write them back into the table. Pay careful attention of what gpart tells you, if it looks wrong don't let it do it.

If gpart fails to find a partition you may still be able to recover files if you need to.

---

### Post by taurus on 2008-02-12
> **giorgione said:**
> Thank you. The partition table on sdb is gone as you thought. gpart is running righ now.... but I was asking myself how did I screw up?
Will ```
 fsck /dev/sdb
``` always erase the partition table on sdb? I find this strange ...?

You should have ran it as

```
fsck /dev/sdb1
```

---

### Post by giorgione on 2008-02-14
I tried to recover my partion table several times with gpart. I did
```
sudo gpart /dev/sdb
sudo gpart  -f /dev/sdb
```

and

```
 sudo gpart -C 60801,255,63 /dev/sdb 

Begin scan...
End scan.

Checking partitions...
Ok.

Guessed primary partition table:
Primary partition(1)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

Primary partition(2)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

Primary partition(3)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

Primary partition(4)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

```

but the results where always the same. :-(
Do I miss something? Are there other ways to recover the data?

---

