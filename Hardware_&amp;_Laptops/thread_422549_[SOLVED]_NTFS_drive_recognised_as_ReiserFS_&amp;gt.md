---
title: "[SOLVED] NTFS drive recognised as ReiserFS &amp;gt; had Reiser before now NTFS formatted"
date: 2007-04-25
forum: Hardware &amp; Laptops
---

### Post by djamu on 2007-04-25
After ( full not quick ) formatting my external 500GB drive back to NTFS, the system still initially recognizes it as ReiserFS, can even open the files that where previously on it, seems some superblocks didn't erase even after a full (? I know even an hour is to short to wipe all blocks ) NTFS format. unmounting it & mounting with #mount -t ntfs /dev/sdxn mounts it read only ( NTFS-3G installed & working as I have other HD's with NTFS ).
I went back to windows, wrote some large files on it...
Still Ubuntu initially sees it as ReiserFS. 
( & can mount it as NTFS read only ... )

dmesg | tail shows me...

```

root@feisty:/# dmesg | tail
[  138.885491] ReiserFS: sdc1: found reiserfs format "3.6" with standard journal
[  138.885837] ReiserFS: sdc1: using ordered data mode
[  138.888862] ReiserFS: sdc1: warning: sh-461: journal_init: wrong transaction max size (3218180121). Changed to 1024
[  138.888871] ReiserFS: sdc1: journal params: device sdc1, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 380935950, max trans age 30
[  138.890243] ReiserFS: sdc1: checking transaction log (sdc1)
[  140.149268] ReiserFS: warning: is_tree_node: node level 46089 does not match to the expected one 2
[  140.149276] ReiserFS: sdc1: warning: vs-5150: search_by_key: invalid format found in block 32770. Fsck?
[  140.149282] ReiserFS: sdc1: warning: vs-13070: reiserfs_read_locked_inode: i/o failure occurred trying to find stat data of [1 2 0x0 SD]
[  140.149701] ReiserFS: sdc1: Using r5 hash to sort names
[  140.149782] ReiserFS: sdc1: warning: xattrs/ACLs enabled and couldn't find/create .reiserfs_priv. Failing mount.
root@feisty:/# 


```


I just want to get rid of any ReiserFS traces & need it to be NTFS ( portability ), I used ext3 before with the windows ext2 driver ( works great ), but since NTFS-3G became stable I don't see any further use ( again portability ).

any advice please

---

### Post by tejster24 on 2007-04-25
You could use dd to wipe the drive completely - it'll fill it with zeroes.

If you do something like the following:

sudo dd if=/dev/zero of=/dev/sdc bs=10M

This will take absolutely forever though.

---

### Post by Ace2016 on 2007-04-25
Yup that DD wil take forever

Have you tried modifying your fstab and telling it that its ntfs?

---

### Post by djamu on 2007-04-25
> **tejster24 said:**
> You could use dd to wipe the drive completely - it'll fill it with zeroes.

If you do something like the following:

sudo dd if=/dev/zero of=/dev/sdc bs=10M

This will take absolutely forever though.

I thought about it, but that will take about 8 hours on a 500gb drive :-k 
It might just be enough to zero the first GB's so the first remaining superblocks and references are destroyed


> **Ace2016 said:**
> Yup that DD wil take forever

Have you tried modifying your fstab and telling it that its ntfs?

Yes sure that works and I can read from it, but it doesn't change the fact that I have now a partition with 2 filesystems on it :lolflag: 
Besides that It should work flawlessly on other computers to ( it's a USB disk )

thanks for the replies

---

### Post by tejster24 on 2007-04-25
Have you looked at the disk in something like cfdisk or fdisk?

Try running

sudo fdisk /dev/sdc

and using the command p to to check the partition type. Does it say HPFS/NTFS?

---

### Post by djamu on 2007-04-25
> **tejster24 said:**
> Have you looked at the disk in something like cfdisk or fdisk?

Try running

sudo fdisk /dev/sdc

and using the command p to to check the partition type. Does it say HPFS/NTFS?

Yes it says HPFS/NTFS, I'm quite sure ( and will verify this ) that the auto mounter & mount commando uses a different approach on detecting file systems ( although strange, this makes sense as it then is able to mount & fix corrupt file systems other then NTFS wich is non native )
So it's not a bug, it's just something annoying that I stumbled upon.

I'll check whether this happens with smaller disks to ( the larger ones use sparse superblocks - that is on ext3 -, don't know enough yet of reiser ) so the layout might differ regarding to size..

I'll just wipe it


thanks again.

---

