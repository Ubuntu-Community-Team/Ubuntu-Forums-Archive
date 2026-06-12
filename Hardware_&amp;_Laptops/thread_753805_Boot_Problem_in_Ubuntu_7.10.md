---
title: "Boot Problem in Ubuntu 7.10"
date: 2008-04-13
forum: Hardware &amp; Laptops
---

### Post by jide on 2008-04-13
Hello, 

I have a dual boot system (windows xp and ubuntu 7.10) on my HP laptop. On my HD are different partitions (NTFS, EXT3 and FAT32 which is visible on both operating systems). I decided to resize the NTFS by taking some space from FAT32 using PartitionMagic 8.0 in Windows but it failed. 

After then, I tried my best to repair it and later when I started Ubuntu it failed. It says hat their might be a corrupt EXT2 and that I should re-run the superblock this way "e2fsck -b 8193 <device>.

I tried the above command but it failed. I am yet to try the next superblock which is 32768 because I am afraid to damage my HD further.

Can someone help me out with a good solution.

Thanks.

---

### Post by Liunx on 2008-04-13
:popcorn:
may the best solution is that :
you ready a cd for recovery!
and boot it from cdrom ,mount the root filesystem,and chroot in it,after that ,
do your recovery ,may be more effective.
thank you !

---

### Post by jide on 2008-04-13
Hello,

I used a live CD but the problem is still there. I first tried: *fdisk -l /dev/hda* to know if hda7 exits and I got: */dev/hda7 7924 (Start) 9139 (End) 9767488+ (Blocks) b (ID) W95 FAT32 (System)*. So the partition exists. I ran *sudo e2fsck -b 8193 /dev/hda7 * and also used the following alternate superblocks, 32768, 98304, 163840, 229376 and 294912 but all failed. I do not know the next line I can take. Any help?


Note: Below is the initial error message when ubuntu boots.
[I]/dev/hda7: 2414 files, 52997/610168 clusters
fsck.ext3: Bad magic number in super-block while trying to open /dev/hda7

The superblock could not be read or does not describe a correct ext2 filesystem. If the device is valid and it really contains and ext2 filesystem (and not swap or ufs or something else), then superblock is corrupt, and you might try running e2fsck with an alternate superblock:

e2fsck -b 8193 <device>

fsck died with exit status 9[/I]

Thanks for the expected reply.

---

### Post by danwood76 on 2008-04-14
When you say you have NTFS, EXT3 and FAT32 partitions are they on the disk in that order?

If so you wouldnt be able to just take space from the FAT32 and add it to the NTFS as the EXT3 partitions will be in the way.
You would need to relocate the EXT3 partititon aswell as shrinking the FAT and growing the NTFS.

If you boot the live CD can you give the output of:
```

sudo fdisk -l

```

You will always get issues running partition ing software from within a running OS with mounted partitions, its always best to do it from a live CD.

---

### Post by jide on 2008-04-16
> **danwood76 said:**
> When you say you have NTFS, EXT3 and FAT32 partitions are they on the disk in that order?

If so you wouldnt be able to just take space from the FAT32 and add it to the NTFS as the EXT3 partitions will be in the way.
You would need to relocate the EXT3 partititon aswell as shrinking the FAT and growing the NTFS.

If you boot the live CD can you give the output of:
```

sudo fdisk -l

```

You will always get issues running partition ing software from within a running OS with mounted partitions, its always best to do it from a live CD.

Hello,

sudo fdisk -l /dev/hda will give:
[HTML]

Device         Start    End      Blocks	     ID      System
/dev/hda1*      1       4532     3640325     7       HPFS/NTFS
/dev/hda2	4533	9527	40122337+    F       W95 Ext'd(LBA)
/dev/hda3	9528	12161	21157605     83      LINUX
/dev/hda5	4533	5167	5100606      b       W95 FAT32
/dev/hda6	5168	7923	22137538+    b       W95 FAT32
/dev/hda7	7924	9139	9767488+     b       W95 FAT32
/dev/hda8	9140	9266	1020096      83      LINUX
/dev/hda9	9267	9527	2096451      82      LINUX SWAP/SOLARIS

[/HTML]

Thanks for the expected answer.

---

### Post by danwood76 on 2008-04-16
your partition table is pretty messed up.
From the ubuntu live CD install testdisk and run the scan for lost partitions and hopefully it will find your original partition table or at least be abl;e to repair it.

good luck!

---

