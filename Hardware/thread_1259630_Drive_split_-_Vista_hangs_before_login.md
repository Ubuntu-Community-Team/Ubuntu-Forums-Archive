---
title: "Drive split - Vista hangs before login"
date: 2009-09-06
forum: Hardware
---

### Post by bluetang on 2009-09-06
I have vista installed on the first partition, ubuntu on the next, a separate /home partition - all logical, I split existing NTFS partition of 275GB in the Ubuntu live cd. And formatted the pair of 148GB partitions NTFS. Now vista halts loading just short of the login screen with a blank screen.

---

### Post by JC Cheloven on 2009-09-06
1) Although I did it sucesfully sometimes, vista doesn't like to be shrinked externally. When you will, it is advised to defrag first, and if possible, to ask vista himself to liberate some space. Usually it refuses to give away more than 10-15Gb, but that's safer. And I've found less prone to errors to shrink a bit more from that state using gparted from live cd.
I know, the advice comes too late :/

2) All partitions you have are logical ones? It is quite unusual, as in most cases vista comes preinstalled on the first partition, and then you liberate space from there (for an extended one or whatever). Please, post the output of ```
sudo fdisk -l
```

3) I don't use vista, but I guess the first thing you should try is running a recovery console out of your vista installation cd, but I can't give you more advice on this point. It will mess your grub startup, though.

---

### Post by klightspeed on 2009-09-07
I noticed the same fragility when I attempted to split my Vista partition - Bootmgr seems to include the geometry of the partition in its drive UUID calculation, and will fail to boot if the drive geometry is changed without updating /Boot/BCD; Unfortunately, unlike /boot.ini, /Boot/BCD is a registry file with opaque key and value names (not human editable), so you can't just fix it from Linux.

The diskpart utility in Vista is able to shrink NTFS partitions; IIRC it can shrink the partition online, but you will need to use a better defragmenter than that build in (e.g. [Ultimate Defrag](http://www.neowin.net/news/software/08/05/23/ultimatedefrag-freeware-edition-172)) if you want to shrink it much.

If you have a hidden NTFS recovery partition, or you have the Vista disk, you should be able to boot into recovery mode, from which you *should* be able to repair cranky Vista.

---

