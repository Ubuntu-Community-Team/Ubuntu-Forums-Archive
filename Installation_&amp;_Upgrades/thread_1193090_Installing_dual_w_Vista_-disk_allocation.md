---
title: "Installing dual w Vista -disk allocation?"
date: 2009-06-21
forum: Installation &amp; Upgrades
---

### Post by Alligator on 2009-06-21
I'm using [http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=1](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=1)  to install 9.04 (64 bit) I've shrunk D drive in Vista to allow 70G free space.
During the Ubuntu install to prepare the disk space, I was expecting a button option to "Use the largest continuous free space" - not there, as stated in instructions.
I selected manual to avoid deleting Vista, but not allowed to move forward because a root has not been established. Also, not able to select the free space to assign a file system (ext3/ext4)

I'm stuck. Your help would be appreciated.

Laptop Acer 8730.

---

### Post by merlinus on 2009-06-21
This should help:

[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

---

### Post by Alligator on 2009-06-21
I ran the liveCD - partition editor. Here is the result.  Note - this is vista

                   Lable        Size    Used     Unused
unallocated                    1M
/dev/sda1   fat32  PQService   11.72G    10.6      1
/dev/sda2   ntfs   Acer        141.67G   27        113
/dev/sda3   ntfs   DATA        70G
unallocated                    70G
/dev/sda4   ntfs               3          1.4      1.6


I want to put 9.04 in the 70G unallocated space. I think that I need to remove one of the 4 primary part. and make it extended.  BUT, I not sure and definitely don't want to lose Vista.   What needs to be done.  I haven't dealt with partitioning for a very long time.

---

### Post by Gen2ly on 2009-06-21
> **Alligator said:**
> I ran the liveCD - partition editor. Here is the result.  Note - this is vista

                   Lable        Size    Used     Unused
unallocated                    1M
/dev/sda1   fat32  PQService   11.72G    10.6      1
/dev/sda2   ntfs   Acer        141.67G   27        113
/dev/sda3   ntfs   DATA        70G
unallocated                    70G
/dev/sda4   ntfs               3          1.4      1.6


I want to put 9.04 in the 70G unallocated space. I think that I need to remove one of the 4 primary part. and make it extended.  BUT, I not sure and definitely don't want to lose Vista.   What needs to be done.  I haven't dealt with partitioning for a very long time.

Hmm, a bit odd that there is an unallocated space then another partition that follows that.  Just to be clear it would be good to know what tool you used to partition the drive.  

From as it looks now, the partition tables are going to have to be cleaned up a bit before you can install.

My partition table (fdisk -l):

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1306    10485760   27  Unknown
/dev/sda2   *        1307       11504    81915435    7  HPFS/NTFS
/dev/sda3           11505       38913   220162792+   5  Extended
/dev/sda5           11505       18032    52436128+  83  Linux
/dev/sda6           18033       38803   166843026   83  Linux
```

---

### Post by Bucky Ball on 2009-06-21
> **Alligator said:**
> 
                   Lable        Size    Used     Unused
unallocated                    1M
/dev/sda1   fat32  PQService   11.72G    10.6      1
/dev/sda2   ntfs   Acer        141.67G   27        113
/dev/sda3   ntfs   DATA        70G
unallocated                    70G
/dev/sda4   ntfs               3          1.4      1.6


I want to put 9.04 in the 70G unallocated space. I think that I need to remove one of the 4 primary part. and make it extended. 

If you have four primary partitions on the drive, you are absolutely correct. An extended partition can contain theoretically heaps(!) of partitions, but you can only have four primary partitions on a disk. Ubuntu, unlike Windows, doesn't need to be on a primary partition, it can be on a logical drive inside an extended partition.

---

### Post by Mark Phelps on 2009-06-21
> **Alligator said:**
> ... and definitely don't want to lose Vista.  I haven't dealt with partitioning for a very long time.

Given your concern over NOT losing Vista, you should have at least searched these forums for things NOT to do before you went and used the Ubuntu partitioner to shrink Vista.  But, you might be one of the lucky ones who did NOT trash Vista in the process.  So, the first thing to do is boot back into Vista and make sure you did NOT lose it.

That being OK, my suggestion would be to plugin an external drive, copy the contents of the last NTFS partition to that drive, make note of the size of that partition. Download and burn a GParted LiveCD from distrowatch.com. Boot from that CD, remove the NTFS partition, make an Extended partition to fill the now unallocated space, make a Linux swap partition at the end of the unallocated space, size equal to your system memory, make an NTFS partition (logical) next to the swap partition -- using the size figures you saved, and make an Ext3 partition filling the rest -- for Ubuntu. 

Then, reboot using the Ubuntu CD and choose manual partitioning and select the existing partitions.

---

### Post by merlinus on 2009-06-21
+10!!!

When will they ever learn.....  google and the search feature are their best friends.

---

### Post by Alligator on 2009-06-21
Vista is ok and backup was done.  Thanks for the help.  Happy Father's Day.

---

