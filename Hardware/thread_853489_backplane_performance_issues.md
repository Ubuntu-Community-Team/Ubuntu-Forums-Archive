---
title: "backplane performance issues?"
date: 2008-07-08
forum: Hardware
---

### Post by pjkoczan on 2008-07-08
Hi all,

I'm doing some disk and I/O tests (I'm looking to tweak a backup system) and I'm wondering if people have experienced performance issues with disk backplanes.

I'm only able to average about 10 MB/s doing a straight copy from one local disk to another on a server with a backplane. On the other hand, on my desktop machine where I have 2 local disks connected directly to the motherboard (no backplane), I'm able to average close to 30 MB/s.

I've tried doing cp -r, tar, rsync, and still best I've been able to average is about 10 MB/s.

My questions are, has anyone else experienced this, and is there anything that can be done about it? 

Gory details:
- Server: Supermicro 1U server, PDSMI motherboard, 3.4 GHz Pentium D processor, 1 GB DDR2-667 RAM, 2x 80 GB Western Digital SATA. 
- Desktop: Intel 915 Motherboard, 3 GHz Pentium 4 (w/ hyperthreading), 1 GB DDR 400 RAM, 2x 80 GB Western Digital SATA.

The server hardware is better, but it still has significantly poorer data transfer rates, go figure.

Each of them were idle during these tests so the discrepancy is not due to variations in noise.

---

### Post by tamoneya on 2008-07-08
the best way to do harddrive testing IMHO is with hdparm:```
sudo hdparm -t /dev/sda
```
Get some more accurate numbers and then we can try to get to the bottom of it.

---

### Post by pjkoczan on 2008-07-09
> **tamoneya said:**
> the best way to do harddrive testing IMHO is with hdparm:```
sudo hdparm -t /dev/sda
```
Get some more accurate numbers and then we can try to get to the bottom of it.

Thanks for the tip. I also decided to see what dd would net me.

Desktop machine:

```

pete@ator ~ $ sudo hdparm -t /dev/sda

/dev/sda:
 Timing buffered disk reads:  174 MB in  3.02 seconds =  57.54 MB/sec

pete@ator ~ $ dd if=/dev/zero of=/scratch/bigfs/lotsofzero bs=1M count=6144
6144+0 records in
6144+0 records out
6442450944 bytes (6.4 GB) copied, 147.579 seconds, 43.7 MB/s

pete@ator ~ $ dd if=/scratch/bigfs/lotsofzero of=/dev/null bs=1M count=6144 
6144+0 records in
6144+0 records out
6442450944 bytes (6.4 GB) copied, 131.994 seconds, 48.8 MB/s

```

Server:

```

pete@mitchell ~ $ sudo hdparm -t /dev/sda

/dev/sda:
 Timing buffered disk reads:  166 MB in  3.01 seconds =  55.19 MB/sec

pete@mitchell ~ $ dd if=/dev/zero of=/scratch/bigfs/lotsofzero bs=1M count=6144
6144+0 records in
6144+0 records out
6442450944 bytes (6.4 GB) copied, 401.267 seconds, 16.1 MB/s

pete@mitchell ~ $ dd if=/scratch/bigfs/lotsofzero of=/dev/null bs=1M count=6144
6144+0 records in
6144+0 records out
6442450944 bytes (6.4 GB) copied, 144.417 seconds, 44.6 MB/s

```

Weird, it appears to be reading fast, but writing really slowly. Also weird is that when I try to read from disk and write to a network connection (over an ssh pipe or trying to copy to AFS), it averages ~25 Mbit/s and peaks  at ~40 Mbit/s, even though these machines are on a Gigabit network. If the disk I/O were the limiting factor, you'd expect it to average about 400 Mbit/s.

---

### Post by tamoneya on 2008-07-09
what type of filesystem to you have on the backplane?

---

### Post by pjkoczan on 2008-07-09
> **tamoneya said:**
> what type of filesystem to you have on the backplane?

ext3 on both machines.

---

### Post by tamoneya on 2008-07-09
This is getting a little bit out of my knowledge so I am not exactly sure what to look for but we may as well take a look at the filesystem parameters.  Post the results of running this on both disks:```
sudo tune2fs -l /dev/sda1
```

---

### Post by pjkoczan on 2008-07-09
> **tamoneya said:**
> This is getting a little bit out of my knowledge so I am not exactly sure what to look for but we may as well take a look at the filesystem parameters.  Post the results of running this on both disks:```
sudo tune2fs -l /dev/sda1
```

No major differences, as near as I can figure. I might be able to tweak some BIOS settings, but other than that, I'm still at a loss. Thanks for all your help.

Desktop:

```

pete@ator ~ $ sudo tune2fs -l /dev/sda1
tune2fs 1.39 (29-May-2006)
Filesystem volume name:   /
Last mounted on:          <not available>
Filesystem UUID:          faccf252-df6e-4453-80c2-3faf4d024bf7
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal resize_inode dir_index filetype needs_recovery sparse_super large_file
Default mount options:    user_xattr acl
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              14567520
Block count:              14554882
Reserved block count:     727744
Free blocks:              14032302
Free inodes:              14567146
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      1020
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         32736
Inode blocks per group:   1023
Filesystem created:       Thu Dec 20 16:16:32 2007
Last mount time:          Tue Jun 24 16:02:11 2008
Last write time:          Tue Jun 24 16:02:11 2008
Mount count:              18
Maximum mount count:      -1
Last checked:             Thu Dec 20 16:16:32 2007
Check interval:           0 (<none>)
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:               128
Journal inode:            8
Default directory hash:   tea
Directory Hash Seed:      614c0179-3a83-42cb-a562-93548a7b918b
Journal backup:           inode blocks

```

Server:

```

pete@mitchell ~ $ sudo tune2fs -l /dev/sda1
tune2fs 1.39 (29-May-2006)
Filesystem volume name:   /
Last mounted on:          <not available>
Filesystem UUID:          1e4ec96f-ad93-4468-ae45-b562f0ecb543
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal resize_inode dir_index filetype needs_recovery sparse_super large_file
Default mount options:    user_xattr acl
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              14567520
Block count:              14554882
Reserved block count:     727744
Free blocks:              14015704
Free inodes:              14567491
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      1020
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         32736
Inode blocks per group:   1023
Filesystem created:       Wed Apr  2 15:47:55 2008
Last mount time:          Sat Apr  5 01:00:18 2008
Last write time:          Sat Apr  5 01:00:18 2008
Mount count:              7
Maximum mount count:      -1
Last checked:             Wed Apr  2 15:47:55 2008
Check interval:           0 (<none>)
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:               128
Journal inode:            8
Default directory hash:   tea
Directory Hash Seed:      c73590ed-c670-423f-89bf-50d77ffef79e
Journal backup:           inode blocks

```

---

### Post by tamoneya on 2008-07-10
unfortunately it looks all normal to me as well.  At this point I would think about looking into drivers for the SATA controller.

---

### Post by pjkoczan on 2008-07-10
> **tamoneya said:**
> unfortunately it looks all normal to me as well.  At this point I would think about looking into drivers for the SATA controller.

Sounds like as good a plan as any. Thanks for your help.

---

