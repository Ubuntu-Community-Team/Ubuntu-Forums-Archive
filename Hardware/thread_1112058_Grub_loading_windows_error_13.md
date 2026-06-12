---
title: "Grub loading windows: error 13"
date: 2009-03-31
forum: Hardware
---

### Post by TheJimtasticOne on 2009-03-31
OK, I've got a dual boot with ubuntu on /dev/sda1 and I've just installed windows on /dev/sda2. After the installation, the windows bootloader came up, so I used the ubuntu livecd to reinstall grub on there. There's now an entry for windows, but selecting it gives:
```
Grub Error 13: Invalid or unsupported executable format
```

menu.lst entry:
```
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader	+1
```

fdisk -l:
```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000dc7e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        5222    41945683+  83  Linux
/dev/sda2   *        5223       10444    41945715    7  HPFS/NTFS
/dev/sda3           10445       30401   160304602+   5  Extended
/dev/sda5           10445       29748   155059348+  83  Linux
/dev/sda6           29749       30401     5245191   82  Linux swap / Solaris

```

Any ideas, anyone?

---

### Post by coffeecat on 2009-03-31
You've got the grub partition numbering wrong, and you don't need the map command when you put Windows on sda - only for sdb.

I think you need:

```
title        Microsoft Windows XP Home Edition
rootnoverify    (hd0,1)
savedefault
chainloader    +1
```
 or

```
title        Microsoft Windows XP Home Edition
root        (hd0,1)
savedefault
makeactive
chainloader    +1
```

or some permutation of the two. Ubuntu sets up menu.lst for Windows differently with different releases it seems. Just experiment until it works. :wink:

**Edit:** What was happening with your code was that Grub was looking for Windows on sdb1 rather than on sda2.

hd(1) = sdb ; hd(1,0) = sdb1 ; hd(0,1) = sda2. You can work the rest out.

---

### Post by meierfra. on 2009-03-31
The correct entry is:

title		Microsoft Windows XP Home Edition
root		(hd0,1)
chainloader	+1

---

### Post by TheJimtasticOne on 2009-04-01
Thanks everyone! This worked:

```
title Microsoft Windows XP Home Edition
root (hd0,1)
chainloader +1
```

---

### Post by meierfra. on 2009-04-01
Great it worked out. Actually both the entries suggested by coffeecat would work,too (we posted at the same time). Have fun with XP and Ubuntu.

---

### Post by thongkh on 2009-12-30
i also have the same problem, Grub have error 13 when loading window xp

my fdisk -l
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf07ff07f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6079    48829536   83  Linux
/dev/sda2            6080       19457   107458785    5  Extended
/dev/sda5            6080       18706   101426314+  83  Linux
/dev/sda6           18707       19457     6032376   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x571b4383

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       26109   209720511    7  HPFS/NTFS
/dev/sdb2           26110      121601   767039490    f  W95 Ext'd (LBA)
/dev/sdb5           26110       52218   209720511    b  W95 FAT32
/dev/sdb6           52219       78327   209720511    7  HPFS/NTFS
/dev/sdb7           78328      121601   347598373+   7  HPFS/NTFS

```

my menu.lst
```
title        WinXP Pro
rootnoverify    (hd0,0)
savedefault
chainloader    +1

```

after i have read through the previous post, i change my menu.lst to
```
title        WinXP Pro
rootnoverify    (hd1,0)
savedefault
chainloader    +1
```
it show
```
starting...
_
```
but system no longer respond :confused:, i have to poweroff then power on again, after that result still same. but if i change my hdd boot priority to my window hdd, window xp boot fine.

need help on this.

thankz.

---

### Post by meierfra. on 2009-12-30
Use

title        WinXP Pro
rootnoverify    (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader    +1

---

### Post by thongkh on 2009-12-30
> **meierfra. said:**
> Use

title        WinXP Pro
rootnoverify    (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader    +1

thankz dude... this fixed my problem\\:D/

but where can i find information about what should be the correct commend? like to learn more about it :D

---

