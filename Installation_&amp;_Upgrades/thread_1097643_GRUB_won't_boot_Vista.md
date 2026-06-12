---
title: "GRUB won't boot Vista"
date: 2009-03-16
forum: Installation &amp; Upgrades
---

### Post by Etamami on 2009-03-16
Hey everyone!

I just installed Ubuntu 8.10. During the install it didn't set up grub, so I picked it to install on the drive. Vista booted up properly after, but since I istalled all updates on Ubuntu, it's just won't! :(

If I hit the Vista line, it says:
**ERROR 22: No such partition.**

Previously I had Vista allready up. I just post my result of
$ sudo fdisk -l result
```
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbfc572e8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       13054   104856223+   7  HPFS/NTFS
/dev/sda2           13055       24321    90502177+   7  HPFS/NTFS

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7985de40

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       91202   732571648    7  HPFS/NTFS

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbc750afb

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdd: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd9218c93

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1        7833    62914560    7  HPFS/NTFS
/dev/sdd2            7834        9700    14996677+  83  Linux
/dev/sdd3            9701        9964     2120580    5  Extended
/dev/sdd5            9701        9964     2120548+  82  Linux swap / Solaris

```

sda = for storage
sdb = also
sdc = not partitioned yet
sdd = with OS-es as you can see

Now I post the line for Vista in my menu.lst from GRUB.

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows Vista/Longhorn (loader)
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```

What's the problem??? Why won't vista not boot?

---

### Post by Etamami on 2009-03-16
*PS: When I istalled Ubuntu vista booted up properly, but since I did the updates on Ubuntu, now it's not working!*

---

### Post by Mark Phelps on 2009-03-16
According to your fdisk result, Vista is not on hd1, it's on hd3 (remember, GRUB counts from zero, not one). Change all your hd1 to hd3 in the Vista stanza and see if that works.

---

### Post by Etamami on 2009-03-16
OK! I will try it in 1 sec.

Actually, it's funny, because since I updated the order of drives has changed, because previously it was hd1! Strange! :rolleyes:

---

### Post by Etamami on 2009-03-16
OK!

I changed to:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows Vista/Longhorn (loader)
root		(hd3,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
```

Not it says:
[B][SIZE="5"]Strating up...

BOOTMGR is missing[/SIZE][/B]

What's this?

---

### Post by Etamami on 2009-03-16
I google this "BOOTMGR" thing. I booted up Vista DVD, run command prompt with this:
$ bootrec /fixboot
succesfully.

Still, Vista won't boot up, says it's missing.

Any ideas what's the problem?

I try not this in GRUB menu.lst:
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows Vista/Longhorn (loader)
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

title		Windows Vista SP1
root		(hd0,0)
chainloader	+1

title		Windows Vista Ultimate
root		(hd2,0)
chainloader	+1

title		Windows Vista
root		(hd3,0)
chainloader	+1
```

---

### Post by mhgsys on 2009-03-16
> **Etamami said:**
> OK!

I changed to:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows Vista/Longhorn (loader)
root		(hd3,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
```

Not it says:
[B][SIZE="5"]Strating up...

BOOTMGR is missing[/SIZE][/B]

What's this?

try ```


title		Windows Vista/Longhorn (loader)
root		(hd3,0)
savedefault
makeactive
map		(hd0) (hd3)
map		(hd3) (hd0)
chainloader	+1


```

---

### Post by Etamami on 2009-03-16
OK!

Well, my try was right. Because actually the OS hdd, which is according to fdisk sdd...so the hd3, is during boot the hd0, so basicly it's sda.

My setup in GRUB simply let me pick whick, and it looks like the winner is:
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows Vista
root		(hd0,0)
makedefault
makeactive
chainloader	+1
```

---

### Post by Mark Phelps on 2009-03-16
I said change ALL the hd1 to hd3 -- which would include the map commands.

But since you fixed it anyway, good for you!

---

### Post by Etamami on 2009-03-16
> **Mark Phelps said:**
> I said change ALL the hd1 to hd3 -- which would include the map commands.

But since you fixed it anyway, good for you!

Thank you!

Yep, I fixed it. Actually, the problem was only that grub numbers the drive in other way then linux. Don't know why...but it's actually hd0 where both OS are.

I will change maybe later everything to hd0 as you suggested, but now it's working fine! =D>

THANKS AGAIN! \\:D/ \\:D/ \\:D/

---

### Post by Mark Phelps on 2009-03-17
As we like to say ... if it's not broke, don't fix it!!

Since the GRUB disk sequence and hd sequence don't match, if hd0 works for you, then be happy with that.  Don't know why the sequences don't match, but GRUB has its own way of identifying drives.

---

### Post by Etamami on 2009-03-17
> **Mark Phelps said:**
> As we like to say ... if it's not broke, don't fix it!!

Since the GRUB disk sequence and hd sequence don't match, if hd0 works for you, then be happy with that.  Don't know why the sequences don't match, but GRUB has its own way of identifying drives.

Well, it was broke! :P It didn't boot...so it was! ;) But yeah, anyways, with help I figured it out. :P

---

