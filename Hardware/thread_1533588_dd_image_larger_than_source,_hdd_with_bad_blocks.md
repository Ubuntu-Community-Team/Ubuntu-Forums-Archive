---
title: "dd image larger than source, hdd with bad blocks"
date: 2010-07-18
forum: Hardware
---

### Post by sirkubax on 2010-07-18
Hello, 

I have a hdd that has fallen, and I'm 99% sure it does contain bad blocks.
Before checking it with "badblock" program, i would like to make a dd copy, but i have big problem.

Normal dd did not work (i/o reading errors), so i lunched it with conv=noerror,sync flag

```
dd if=/dev/sdb conv=noerror,sync bs=4096k|pv| dd of=usb320.dd conv=noerror,sync bs=4096k > dd320.LOG
```

but **the image source, took all empty space i had left on my destination drive (406GB), eventhough source hdd is 320GB** so the image is larger than the source drive

source disk (320GB):
```

root@gamma:/home/jacek# fdisk -l /dev/sdb

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5517132d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         262     2098176   27  Unknown
/dev/sdb2   *         263        5485    41948749    7  HPFS/NTFS
/dev/sdb3            5486       38913   268510410    f  W95 Ext'd (LBA)
/dev/sdb5           12037       38913   215889502+  83  Linux
/dev/sdb6            8696       12036    26836551    b  W95 FAT32
/dev/sdb7            5486        6377     7164927   83  Linux
/dev/sdb8            6378        6499      979933+  82  Linux swap / Solaris

Partition table entries are not in disk order


```

I assume than the image file (usb320.dd) is incorrenct.
I have tried also ddrescue, with the same result
```
dd_rescue /dev/sdb usb320.dd -l dd320.LOG 

```

now I'm trying dd without bs flag (so bs=512)
```
dd if=/dev/sdb conv=noerror,sync |pv| dd of=usb320.dd conv=noerror,sync  > dd320.LOG
```
but i'm pretty sure it will also fail

that's also interesting - there is no content in logfile (I suppose some error message should be sent there)

Do you have any idea what can cause this strange problem?

system - Ubuntu Server, 2.6.31-16-generic-pae

sirkubax

---

### Post by sirkubax on 2010-07-19
Ok, i think i have found a bug in dd

I finally manage to make a backup with dd comand, and default bs size (512)
I guess that flags conv=noerror,sync + badBlocks + bs other than sector size, produce bad image disc (probably dd and ddrescue bug)

My disc contain about 2GB bad blocks (around 112Gbyte sector)
thoese 4194304 sectors, exchenged (due to sync flag) for empty sectors in image file, would be:
with bs=4096k: 4194304 * 4096k = 17592GB (that would definitely not fit on my disk :) )
with bs=512: 4194304 * 512 = 2147MB (thats ok)

I guess that while doing synchronization, dd does not check if block size, that it is replacing, are the same, and that's cause problem

I hope that someone will find this usefull in future
I was totally supprised what is going on

sirkubax

---

### Post by cathune on 2011-05-15
Indeed, I find your post very useful. Thanks :-)

---

