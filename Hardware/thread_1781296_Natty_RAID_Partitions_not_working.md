---
title: "Natty: RAID Partitions not working"
date: 2011-06-13
forum: Hardware
---

### Post by Abaddon on 2011-06-13
I've recently bought a new computer, and had a few dramas getting Win7 to play nice with Natty.

Hardware:  
  SSD with Win7/Ubuntu/Home;
  2x 2Tb HDD in Motherboard Intel RAID
      - one partition for Win7 games
      - the other as a shared partition between W7/Natty.

First run through, it seemed to work OK, but I had to reinstall windows 7 - requiring a complete reformat.  On the redo install, Ubuntu won't recognise the RAID.  It works fine in Windows, so I'd like to avoid reformatting it again if at all possible.

/dev/sdb and /dev/sdc are the RAID drives.

Various terminal outputs below:

Can anyone help?

```
cat /etc/fstab:

proc /proc proc nodev,noexec,nosuid 0 0
UUID=8ffac6e9-7dc2-4282-ad6f-59185183b455 / ext4 errors=remount-ro 0 1
UUID=a9c59734-53c6-4c93-9189-6e0ad46a1c62 /home ext4 defaults 0 2
UUID=AAD03FA0D03F71A5 /media/windows ntfs-3g defaults,nosuid,nodev,locale=en_AU.UTF-8 0 0
UUID=8af5ddcd-1fba-46ba-946a-8d536d43fd25 none swap sw 0 0

```

```
cat /etc/mtab:

/dev/sda5 / ext4 rw,errors=remount-ro,commit=0 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
none /dev devtmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
/dev/sda1 /media/windows fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0
/dev/sda6 /home ext4 rw,commit=0 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
/home/trent/.Private /home/trent ecryptfs ecryptfs_cipher=aes,ecryptfs_key_bytes=16,ecryptfs_unlink_sigs,ecryptfs_sig=3578c6971d496563,ecryptfs_fnek_sig=50a244953b9d00eb 0 0
gvfs-fuse-daemon /home/trent/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=trent 0 0

```

```
blkid:

/dev/sda1: UUID="AAD03FA0D03F71A5" TYPE="ntfs" 
/dev/sda5: LABEL="ubuntu" UUID="8ffac6e9-7dc2-4282-ad6f-59185183b455" TYPE="ext4" 
/dev/sda6: LABEL="home" UUID="a9c59734-53c6-4c93-9189-6e0ad46a1c62" TYPE="ext4" 
/dev/sdb: TYPE="isw_raid_member" 
/dev/sdc: TYPE="isw_raid_member" 
/dev/mapper/cryptswap1: UUID="2871d8be-24da-4257-bb9c-a2d466366ecf" TYPE="swap" 

```

```
Output from gparted in terminal:

======================
libparted : 2.3
======================
Could not stat device /dev/md/RAID - No such file or directory.
Could not stat device /dev/md/RAID - No such file or directory.
The backup GPT table is not at the end of the disk, as it should be.  This might mean that another operating system believes the disk is smaller.  Fix, by moving the backup to the end (and removing the old backup)?
Not all of the space available to /dev/mapper/isw_bgeiebgiac_RAID appears to be used, you can fix the GPT to use all of the space (an extra 264 blocks) or continue with the current setting? 
Cannot have overlapping partitions.
The backup GPT table is not at the end of the disk, as it should be.  This might mean that another operating system believes the disk is smaller.  Fix, by moving the backup to the end (and removing the old backup)?
Not all of the space available to /dev/sdb appears to be used, you can fix the GPT to use all of the space (an extra 6320 blocks) or continue with the current setting? 
The backup GPT table is not at the end of the disk, as it should be.  This might mean that another operating system believes the disk is smaller.  Fix, by moving the backup to the end (and removing the old backup)?
Not all of the space available to /dev/sdc appears to be used, you can fix the GPT to use all of the space (an extra 6320 blocks) or continue with the current setting? 

```

---

### Post by psusi on 2011-06-13
Post the output from these commands:

sudo dmraid -ay
ls /dev/mapper

---

### Post by Abaddon on 2011-06-14
```
sudo dmraid -ay
RAID set "isw_bgeiebgiac_RAID" already active
```

```
ls /dev/mapper
control  cryptswap1  isw_bgeiebgiac_RAID
```

---

### Post by psusi on 2011-06-14
What about sudo fdisk -l isw_bgeiebgiac_RAID?

It looks like your array is > 2 TB in size, so you must be using GPT instead of the MSDOS partition table, which is currently not supported on fakeraid.

---

### Post by Abaddon on 2011-06-14
that doesn't give any output back at all.

---

### Post by psusi on 2011-06-14
Sorry, that should have been sudo fdisk -l /dev/mapper/isw_bgeiebgiac_RAID

---

### Post by Abaddon on 2011-06-15
```
WARNING: GPT (GUID Partition Table) detected on '/dev/mapper/isw_bgeiebgiac_RAID'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/mapper/isw_bgeiebgiac_RAID: 2000.4 GB, 2000395833344 bytes
255 heads, 63 sectors/track, 243200 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

                          Device Boot      Start         End      Blocks   Id  System
/dev/mapper/isw_bgeiebgiac_RAID1               1      243201  1953511555+  ee  GPT

```

---

### Post by psusi on 2011-06-15
Yep; GPT is the problem.

---

