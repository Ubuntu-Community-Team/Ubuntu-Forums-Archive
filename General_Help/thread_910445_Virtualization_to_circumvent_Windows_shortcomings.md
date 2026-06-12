---
title: "Virtualization to circumvent Windows shortcomings"
date: 2008-09-04
forum: General Help
---

### Post by Caedis on 2008-09-04
I am looking to create a reliable storage system. I plan to have a RAID 1 array consisting of 2x 1Terrabyte drives. Due to hardware/software constraints I won’t get into here, I cannot install Ubuntu on the bare metal of the system. I am forced to use Windows Vista.

My question is this, if I were to install VMware on the system and use a pre-allocated disk for the VM that would take up as much of the 1TB available as it could, would this circumvent the NTFS fragmentation issue?  Does the pre-allocated disk ignore NTFS’ inherent fragmentation issue?

I have looked into using EXT2/3 drivers for vista and they are very lack luster to say the least. From what I’ve seen, you can read/write to the ext3 system but the nice journaling system is basically turned off or unable to operate. So these are not an option unless full EXT3 with journaling can, without any doubt, be enabled. (Which I doubt)

The bottom line is I hate that I’m having to install Windoze on this system, and I want to make the best of it by using Linux for the lions share of the storage space (as I don’t really trust windows to maintain the terabyte over the long run like EXT3 could do)

Please Help!

---

### Post by bingoUV on 2008-09-04
Is read/write performance for this raid 1 array very critical for you? If not, you could do this

1. Install windows, leave a large NTFS partition
2. On this large NTFS partition, install VMWARE, and Ubuntu on it. Use ext3/XFS/JFS whichever you like for storing data for this Ubuntu. Make this a VMWARE image of constant, static size such that fragmentation of this file is not much of an issue.
3. From windows, scp the data out of the Ubuntu running on the same machine using VMWARE.

This has lots of overhead, but the whole VMWARE image is a single file which does not change in size so there won't be any fragmentation. In my opinion, the advantage gained by absence of fragmentation will be lost in overhead to VMWARE + Ubuntu.

I just suggest you store all your data in NTFS, and run periodic online defragmentation of NTFS

---

### Post by Caedis on 2008-09-04
I was worried that might be an issue. I&#8217;m just hesitant to trust windows with that much contiguous data. I mean, yes it is a RAID 1 array. But the safety of such a high volume of data would seem to need something with a bit for juice than windows and NTFS. I guess I&#8217;m just spoiled on Ubuntu, and the idea of using Windows to store all my sensitive data is a bit scary.

Would having a separate machine to basically be an Ubuntu powered NAS be worthwhile? I&#8217;m worried the overhead of the wireless N network I have here might slow down the transfer of data from the Ubuntu box to the Vista MCE.

Oh, I forgot to mention, this 2 terabyte array will have vast stores of my digitized movies, music, and general storage hogging media. So it would need to be reasonably fast, but still be very reliable, as recovering a terabyte of data would prove&#8230; painful.

---

### Post by bingoUV on 2008-09-04
If I had the luxury of another machine, I would have 

1. Installed windows on the main machine (you said you are being forced to do this, so)

2. Another low profile machine (but with SATA ports and at least 1GB RAM). Install OpenSolaris on this machine.

3. ZFS on this OpenSolaris machine, and made a ZFS pool out of both the 1TB hard disks in raid 1 style.

4. Accessed this in windows through ftp (maybe there is some ftpfs for windows, not sure). Never liked samba/windows share.

*************************

Don't you have wired LAN (1Gbps LAN would be better)? That would cause almost no bottleneck for current hard disk speeds. You can do the above with raid (md) instead of ZFS. It would have a latency, but large file transfers should not be slower than if they were locally available on the windows machine. That is to say, even a small file would take some time to be read/written to but large files would be written almost at full speed.

---

### Post by Caedis on 2008-09-05
Was there some special reason why you would choose OpenSolaris over Ubuntu? What are the specific benefits to ZFS vs EXT3?

---

### Post by bingoUV on 2008-09-05
As you have guessed, opensolaris for the sole reason: ZFS. Otherwise Ubuntu ,or most distros of GNU/linux [sic], blows away opensolaris as a desktop operating system. At least for me.
Too many advantages of ZFS to count. These are off my memory and details are hazy.

1. raid support: Like I said, I would create a raid 1 pool out of both of my 1 TB hard disks. ZFS pools just need to be given hard disks, they manage the raid part themselves. They also dynamically expand, so if your storage needs increase you will add two more 1TB hard disks and the filesystem without needed to be taken offline expands to a 2 TB stoarage area (with 2 raid-1's of 2 hard disks each of 1TB each). Various other possibilities.
With ext3, it will likely be a solution involving md+ext3.

2. Scrubbing: Consider it an online fsck i.e. no need to unmount for integrity checking.

3. Checksumming: Fight against even hardware errors (to some extent, of course) by automatic detection and in some cases correction of errors.

4. Remove(not sure): One of the constituents of your raid 1 giving SMART warnings? Worry not. Detach it from the pool (without unmounting of course) and replace with another disk. Raid-1 will be automatically rebuilt (with performance and failover penalties during the operation). Maybe there is some limitation to this feature about which I am not very sure, but in essence detach is supported.

5. Agonizingly and notoriously slow file deletion for ext3: This is even an advantage in desktop system, but for a server dealing with multiple terabytes it could mean serious loss. Advantage because "sudo rm -rf /", and ctrl-c with ext3 is quite fatal but will lose very little data per second. ZFS may not give you a chance.

To be fair to ext3, it is one generation older than ZFS. That too remarkably backward compatible with a 2 generation old filesystem (ext2). ZFS performs better than ext3, but performance is said to be comparable with ext4, with both having different strong points.

---

### Post by Caedis on 2008-09-05
Thanks for all the advice! I may just have to give Solaris a run and see how it will fit into my plans.

Thanks again Bingo

---

