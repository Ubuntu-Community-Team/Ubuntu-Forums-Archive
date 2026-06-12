---
title: "SSD alignment and RAID set up issues"
date: 2011-10-13
forum: Hardware
---

### Post by moschops on 2011-10-13
This is more of a flowing stream of consciousness on my SSD alignment and RAID setup.  I'm hoping other people trying to figure this stuff out might find my current info useful and perhaps someone who has already got it working well can opine.

#1 Question - can I make SSD + TRIM + RAID work in Ubuntu?
#2 Question - how can I be sure I have alignment correctly setup, mine seems to be blowing.

Anyway, here are the details...

I have a Ubuntu 10.10 based server with three 256GB Cruical C300 SSDs that I spent quite a bit of time researching how to configure properly.  

Eventually I got them set up with software RAID5 and what I thought was correct alignment - I was getting around 300MB/s read and 200MB/s write.   

A year later the same machine is now getting great read performance still at 300MB/s but write is really awful - 50MB/s would be high, sometimes it is more like 20MB/s (measured via iostat during a 'dd' based copy of a large file). I can get better than that from a memory stick over USB!

Since read speeds were still good I think I can rule out controller or non-hardware issues.  Typically one would expect this to be SSD wear - at the time I set it up I was aware that TRIM support is not passed through RAID so this would be a problem.  But I was also under the impression that the Crucial drives have built in "garbage collection" which means TRIM isn't necessary.

After further reading it's still +1 for the C300s having the garbage collection, although I'm at rev2 of the firmware vs rev7.  It is also likely that garbage collection will only work when the drive has enough hints that a block is free.  

I found out about the smartctl program and installed it.  And I found a Crucial document that specfies all the drive specific parameters smartctl can dump:

```
smartcl --all /dev/sdc1
SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   100   100   000    Pre-fail  Always       -       0
  5 Reallocated_Sector_Ct   0x0033   100   100   000    Pre-fail  Always       -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       8113
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       5
170 Unknown_Attribute       0x0033   100   100   000    Pre-fail  Always       -       17668
171 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       0
172 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       0
173 Unknown_Attribute       0x0033   096   096   000    Pre-fail  Always       -       228
174 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       0
181 Program_Fail_Cnt_Total  0x0022   100   100   000    Old_age   Always       -       85899345939
183 Runtime_Bad_Block       0x0032   100   100   000    Old_age   Always       -       0
184 End-to-End_Error        0x0033   100   100   000    Pre-fail  Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   100   100   000    Old_age   Always       -       0
189 High_Fly_Writes         0x000e   100   100   000    Old_age   Always       -       539
195 Hardware_ECC_Recovered  0x003a   100   100   000    Old_age   Always       -       0
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   100   100   000    Old_age   Always       -       0
202 Data_Address_Mark_Errs  0x0018   096   096   000    Old_age   Offline      -       4
206 Flying_Height           0x000e   100   100   000    Old_age   Always       -       0

```

According to the docs param 173 is the average number of times a block has been re-written, and param 202 is the % wear on the drive so I'm still a long way from having worn it out.  More working is param 181 which apparently signifies 85 billion non-4K aligned drive accesses which is something I was trying to avoid when I configured it.

My intention now is to back up all the data on the drives (in RAID 5 it's only 500GB anyway) then use 

```
hdparm --trim-sector-ranges /dev/sdc
```

to issue a trim for all the sectors on the disk and ensure it is zeroed out properly to avoid the slow as molasses erase cycles before each write.

Then I have read that if use LVM over mdraid you can get it to propagate TRIM properly form the raid file system to the underlying device.  I haven't found a really good how to on this so I'm still researching. 

My biggest concern now, to avoid having to redo this activity in 6 months to a year, is those billions of misaligned drive accesses.

Currently I get this out of hdparm:

```
hdparm -I /dev/sdc

/dev/sdc:

ATA device, with non-removable media
	Model Number:       C300-CTFDDAC256MAG                      
	Serial Number:      00000000103602FD2180
	Firmware Revision:  0002    
	Transport:          Serial, ATA8-AST, SATA 1.0a, SATA II Extensions, SATA Rev 2.5, SATA Rev 2.6, SATA Rev 3.0
Standards:
	Used: unknown (minor revision code 0x0028) 
	Supported: 9 8 7 6 5 
	Likely used: 9
Configuration:
	Logical		max	current
	cylinders	16383	16383
	heads		16	16
	sectors/track	63	63
	--
	CHS current addressable sectors:   16514064
	LBA    user addressable sectors:  268435455
	LBA48  user addressable sectors:  500118192
	Logical  Sector size:                   512 bytes
	Physical Sector size:                   512 bytes
	Logical Sector-0 offset:                  0 bytes
	device size with M = 1024*1024:      244198 MBytes
	device size with M = 1000*1000:      256060 MBytes (256 GB)
	cache/buffer size  = unknown
	Form Factor: 2.5 inch
	Nominal Media Rotation Rate: Solid State Device
```

I formated the md0 raid device with ex3 using 4k blocks and an offset such that those blocks should be aligned so I'm really puzzled what went wrong.  Here is the start of the output of tunef2fs on /dev/md0:

```
dumpe2fs 1.41.12 (17-May-2010)
Filesystem volume name:   <none>
Last mounted on:          <not available>
Filesystem UUID:          d7e40a46-ff8f-42e6-809d-20dbda0f4621
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype needs_recovery sparse_super large_file
Filesystem flags:         signed_directory_hash 
Default mount options:    (none)
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              31260672
Block count:              125029056
Reserved block count:     6251452
Free blocks:              23458656
Free inodes:              31237797
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      994
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         8192
Inode blocks per group:   512
RAID stride:              32
RAID stripe width:        64
Filesystem created:       Wed Dec 15 11:39:54 2010
Last mount time:          Wed Oct 12 19:18:29 2011
Last write time:          Wed Oct 12 19:18:29 2011
Mount count:              2
Maximum mount count:      29
Last checked:             Fri Aug 12 17:54:40 2011
Check interval:           15552000 (6 months)
Next check after:         Wed Feb  8 16:54:40 2012
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:	          256
Required extra isize:     28
Desired extra isize:      28
Journal inode:            8
First orphan inode:       25698309
Default directory hash:   half_md4
Directory Hash Seed:      0d750fe1-c189-4647-a673-835efe351596
Journal backup:           inode blocks
Journal features:         journal_incompat_revoke
Journal size:             128M
Journal length:           32768
Journal sequence:         0x00cae4dd
Journal start:            1


Group 0: (Blocks 0-32767)
  Primary superblock at 0, Group descriptors at 1-30
  Reserved GDT blocks at 31-1024
  Block bitmap at 1537 (+1537), Inode bitmap at 1538 (+1538)
  Inode table at 1025-1536 (+1025)
  0 free blocks, 8181 free inodes, 2 directories
  Free blocks: 
  Free inodes: 12-8192
Group 1: (Blocks 32768-65535)
  Backup superblock at 32768, Group descriptors at 32769-32798
  Reserved GDT blocks at 32799-33792
  Block bitmap at 34337 (+1569), Inode bitmap at 34338 (+1570)
  Inode table at 33793-34304 (+1025)
  0 free blocks, 8192 free inodes, 0 directories
  Free blocks: 
  Free inodes: 8193-16384
```

For the record here are my notes on the commands used to originally set up the drives:

```
SSDs are mounted as /dev/sdb /dev/sdc and /dev/sdd and configured with DOS partition table, one partition per disk as per:

http://www.nuclex.org/blog/personal/80-aligning-an-ssd-on-linux
http://www.ocztechnologyforum.com/forum/showthread.php?54379-Linux-Tips-tweaks-and-alignment&p=373226#post373226

First partition has special alignment required alignment for better SD performance.  Created using:

fdisk -H 32 -S 32 /dev/sdb
o # Create partition table (DOS style)
n # New partition
1 # Its the first partition
2 # Second cylinder start
<enter> # Last cyclinder end (take default - fill disk)
t # Set type
fd # RAID auto-detect
w # Write table

Create software RAID. WARNING: erases any current RAID array

mdadm --create /dev/md0 --chunk=128 --level=5 --raid-devices=3 /dev/sdb1 /dev/sdc1 /dev/sdd1 --name=work

Add an ext3 file system to the array with 4k block size and strip and stride sized according to article note number of disks in array is 2 because one is parity only

mkfs.ext3 -b 4096 -E stride=32,stripe-width=64 /dev/md0

Add fs to /etc/fstab using noatime to reduce accesses

/dev/md0 /work ext3 errors=remount-ro,noatime 0 1


```

Since I wasn't expecting TRIM support to work anyway I didn't try to enable it with the 'discard' option in the mount but I think that only works for ext4 which I didn't use at the time as there were supposedly serious bugs in the specific Kernel version in use.  Now I'm ready to upgrade to 11.10 so that shouldn't be a problem any more.

---

### Post by moschops on 2011-10-16
Okay, seems like a lot of people have read this post so far but no comments.  Here is my follow up:

[LIST=1]
[*] I could find no evidence that mdraid can support TRIM and no specific information about RAID and the C300 drives.
[*] I decided that RAID-5 is nice but not worth the performance hit, this is, after all, supposed to be a rocket-sled of a server
[*] I went with a 3-stripe LVM setup based on the info here which is pretty recent and widely referenced: [http://www.ocztechnologyforum.com/forum/showthread.php?82648-software-RAID-LVM-TRIM-support-on-Linux](http://www.ocztechnologyforum.com/forum/showthread.php?82648-software-RAID-LVM-TRIM-support-on-Linux) - the only changes were to use a single partition per drive (no Raid boot partition was required), 3 stripes not two (since I have three disks) and use 100%VG instead of a number in the extents param of the lvcreate command.
[*] I got the FS tuning info that changes the raw disk block access scheduler used from here: [http://www.howtogeek.com/62761/how-to-tweak-your-ssd-in-ubuntu-for-better-performance/](http://www.howtogeek.com/62761/how-to-tweak-your-ssd-in-ubuntu-for-better-performance/) - it is similar to info in the ocz forum page.
[/LIST]

Oh and step 2 1/2 which you can probably leave out - I used hdparm on-liner from here: [http://superuser.com/questions/283590/restoring-performance-and-estimating-life-of-a-used-ssd-drive](http://superuser.com/questions/283590/restoring-performance-and-estimating-life-of-a-used-ssd-drive) to issue a trim for the entire disk.  I believe this is redundant because the ext4 format should do this for you (according to the OCZ forum post).

After formatting I was able to do a 10GB file create on the new volume at 700MB/s :-)  I'm pretty sure my I/O is now limited by the mobo SATA2 controllers on our Dell server.  I have some SATA3 cards waiting to be installed.

Also since setting up the drive I have been monitoring the drive and there are no longer an non 4K-aligned disk access on any of the drives.  Yay, looks like I got things right this time.

So my next task is that now I have a 3 disk RAID-0 setup I need to set up rsnapshot based backup of the disk.  rsnapshot can handle doing an LVM snapshot around the backups for a completely consistent backup.  See here for details:

[http://tldp.org/HOWTO/LVM-HOWTO/snapshots_backup.html](http://tldp.org/HOWTO/LVM-HOWTO/snapshots_backup.html)

If you have any specific questions just post a reply!

EDIT: I have seen that I should have probably made my logical volume < 100% of the volume group to leave from for a backup snapshot.  A 10% spare should be ample for any backup.  I will make a backup and try an ext4 resize with resize2fs although it may be safer to just recreate the logical volume at 90% and recreate a new file system.

---

