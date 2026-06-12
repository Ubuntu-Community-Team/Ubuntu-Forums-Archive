---
title: "USB BUG? Impossible to create ext3/4 fs on USB Disk"
date: 2010-08-03
forum: Hardware
---

### Post by asbesto on 2010-08-03
Hi, after 3 attempts with 3 different 8GB USB Keys, I'm here showing you this incredible problem.

A fresh 8GB USB flash disk. HP INVENT USB 2.0, 8GB key, model number v115W

I plug in my computer, it will open an empty folder, FAT32 formatted. Perfectly working. OK.

Now, I *need* to format it in ext3 or ext4 to use as /home in my asus eeepc 701-4g.

So, I open cfdisk, that suddendly give me this error:

```
FATAL ERROR: Bad primary partition 0: Partition ends in the final partial cylinder
```

I use fdisk instead; clean the partition, create a new one, type 83, active. write, sync.

mkfs.ext3 /dev/sdc1 work and create the filesystem.

A couple of sync, just to be sure

unplug, plug again, and here's the error:

```
Unable to mount 8.5 GB Filesystem
Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sdc1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

dmesg says:

```

[531436.903396] usb-storage: device found at 31
[531436.903401] usb-storage: waiting for device to settle before scanning
[531441.900222] usb-storage: device scan complete
[531441.900948] scsi 31:0:0:0: Direct-Access     Generic  Flash Disk       8.00 PQ: 0 ANSI: 2
[531441.905849] sd 31:0:0:0: Attached scsi generic sg3 type 0
[531441.909879] sd 31:0:0:0: [sdc] 16547840 512-byte logical blocks: (8.47 GB/7.89 GiB)
[531441.910427] sd 31:0:0:0: [sdc] Write Protect is off
[531441.910433] sd 31:0:0:0: [sdc] Mode Sense: 03 00 00 00
[531441.910438] sd 31:0:0:0: [sdc] Assuming drive cache: write through
[531441.914668] sd 31:0:0:0: [sdc] Assuming drive cache: write through
[531441.914676]  sdc: sdc1
[531442.063807] sd 31:0:0:0: [sdc] Assuming drive cache: write through
[531442.063817] sd 31:0:0:0: [sdc] Attached SCSI removable disk
[531442.790126] JBD: no valid journal superblock found
[531442.790131] EXT3-fs: error loading journal.

```

#-o[-o<](*,)#-o

A fsck.ext3 issued on the partition will found TONS of errors. 8(

This is me, creating a fresh new ext3 filesystem and suddendly checking it:

```

root@gemini:~# mkfs.ext3 /dev/sdc1
mke2fs 1.41.11 (14-Mar-2010)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
517120 inodes, 2068479 blocks
103423 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=2118123520
64 block groups
32768 blocks per group, 32768 fragments per group
8080 inodes per group
Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632

Writing inode tables: done                            
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 38 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.
root@gemini:~# fsck.ext3 /dev/sdc1
e2fsck 1.41.11 (14-Mar-2010)
Superblock has an invalid journal (inode 8).
Clear<y>? no

fsck.ext3: Illegal inode number while checking ext3 journal for /dev/sdc1
root@gemini:~# fsck.ext3 /dev/sdc1
e2fsck 1.41.11 (14-Mar-2010)
Superblock has an invalid journal (inode 8).
Clear<y>? yes

*** ext3 journal has been deleted - filesystem is now ext2 only ***

/dev/sdc1 was not cleanly unmounted, check forced.
Pass 1: Checking inodes, blocks, and sizes
Journal inode is not in use, but contains data.  Clear<y>? 

```

this is UNBELIEVABLE :(

I changed 3 fresh new USB 8GB keys and I have the same problem again and agains, on different computers with 10.04 and 9.10 Ubuntu. 

PLEASE SOMEONE HELP, i'm really going NUTS for that :(

---

### Post by marawuti on 2010-08-27
No solution here just recording some similar info for same device.  Hoping someone will see a fix for both of us.

My HP v115w was being used primarily on a Mac OS X <something>, inserted into my Ubuntu 10.04 laptop and added two directories of diving videos.  Returned to the Mac and was totally unusable.

Now on Windoz XP, Ubuntu 10.04, the files are accessible read-only.  They show Unix type privileges, but the device is seen as FAT32.  Mkdosfs fails on the fsync().  Gparted & Disk Utility show failures on fsync() as well when attempting (re)partioning etc.  sudo [chgrp | chmod | chown] fail.

I'm starting to wonder if these devices are particularly fragile electronically.  There seem to be quite a few disparate threads where these are mentioned. ](*,)

---

