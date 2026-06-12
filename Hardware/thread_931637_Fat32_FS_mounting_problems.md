---
title: "Fat32 FS mounting problems"
date: 2008-09-27
forum: Hardware
---

### Post by eleifsp on 2008-09-27
Ok, first, some back story:

I have a laptop with the disk partitioned as follows:

/dev/sda1: NTFS (Windows Vista)
/dev/sda2: NTFS (Windows Vista Recovery disk.  I know, don't ask me.)
/dev/sda3: Ext3 (Ubuntu 8.04.1)
/dev/sda4: Extended partion
/dev/sda5: Ext3 (Currently my Home folder)
/dev/sda6: Swap

sda5 used to be a fat32 partition used to share files between Vista and Ubuntu.  However, I tried upgrading Ubuntu 8.04 to 8.10 alpha, had it fail miserably, and reinstalled Ubuntu 8.04 with this new partition scheme.

Now, before I did so, I reformatted my external hard drive and partitioned it.  I backed up my files from my /home and the /dev/sda5 areas.  The ext hard drive looks like this:

/dev/sdb1: Fat32 (this is where my files are)
/dev/sdb2: Ext3 (I put this here so that I can experiment with other distros without touching my current setup, so it is now unused)

Now, of course, all the files went into the Fat32 file system perfectly.  Less than a day later, I've got my new Ubuntu install working well enough, so I try to mount the hard drive.  The EXT3 mounts perfectly, but of course the system my files are on doesn't.  When trying to mount it (by Nautilus or Terminal) I get the "Can't read superblock" error.  The output of fsck.vfat is:

> dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/
  Contains a free cluster (2). Assuming EOF.
FAT32 root dir starts with a bad cluster!


Does anyone know if I can fix this, or get my files back, or am I just out of luck?

Thanks in advance.

EDIT:

Ok, I have some new info.  I ran dosfsck (with a bunch of flags) and this is what I got:

> sudo dosfsck /dev/sdb1 -a -r -v -V -l -f -t
dosfsck 2.11 (12 Mar 2005)                                     
dosfsck 2.11, 12 Mar 2005, FAT32, LFN                          
Checking we can access the last sector of the filesystem       
There are differences between boot sector and its backup.
Differences: (offset: original/backup)
  65:01/00
1) Copy original to backup
2) Copy backup to original
3) No action
? 2
Boot sector contents:
System ID "MSWIN4.1"
Media byte 0xf8 (hard disk)
       512 bytes per logical sector
     16384 bytes per cluster
        74 reserved sectors
First FAT starts at byte 37888 (sector 74)
         2 FATs, 32 bit entries
  53435392 bytes per FAT (= 104366 sectors)
Root directory start at cluster 2 (arbitrary size)
Data area starts at byte 106908672 (sector 208806)
  13355536 data clusters (218817101824 bytes)
63 sectors/track, 255 heads
        63 hidden sectors
 427585977 sectors total
Starting check/repair pass.
Checking file /
/
  Contains a free cluster (2). Assuming EOF.
FAT32 root dir starts with a bad cluster!


The Man pages state that the exit status of 2 was that it didn't access the file system (which would be true if it didn't get past root).  Is there any way to at least recover my files?  All I really want back are my .doc, .ppt, .jpeg/.gif and .mp3 files.

---

