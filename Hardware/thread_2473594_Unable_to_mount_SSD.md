---
title: "Unable to mount SSD"
date: 2022-04-07
forum: Hardware
---

### Post by dkolars on 2022-04-07
NAME="Ubuntu"
VERSION="20.04.4 LTS (Focal Fossa)"
5.13.0-37-generic

Just got an 8TB SSD USB drive...  Might end up being trash?
I added an internal SSD to my system a year+ ago, and had NO problems like this

Plugged it in, mounted instantly.  Yay
Attempted to copy a  0.6GB file, NOT ENOUGH SPACE.  ???
Checked it the GParted, it's 7.3 TB + extra partition.
Futzed with it, still no go.
Formatted SSD to FAT32.  Nope, still not enuf room. ???  AND, Permissions were root:root.  Can't change permissions with that formatting.
Formatted to Ext4, cannot mount drive!  Get this:
[https://ubuntuforums.org/attachment.php?attachmentid=290253&stc=1](https://ubuntuforums.org/attachment.php?attachmentid=290253&stc=1)
Chown and chmod commands run without errors, but nothing happens.

So, I can format it to any partition type, it would seem, but can't use it.  

Any hints before I attempt to return it?    PIA

TIA  dk

---

### Post by colin-i on 2022-04-08
What f3probe from f3 package is saying there?
```

sudo apt install f3
sudo f3probe -t /dev/sdx #replace x with the drive letter

```

---

### Post by oldfred on 2022-04-08
Please do not post screen shots or photos in line. Easy to add with Forum's advanced editor and paperclip icon.
[https://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098](https://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098)

You should only use FAT32 for smaller partitions. It cannot have a file over 4GB and has no journal making file recovery more difficult or impossible.

Windows formats will always show root as they do not support Linux ownership & permissions. Those are set only by how the partition is mounted.

How did you partition drive?
Post this, if still hdh:
sudo gdisk -l /dev/sdh
sudo fdisk -l

---

### Post by oldos2er on 2022-04-08
> Just got an 8TB SSD USB drive...  Might end up being trash?

I would try deleting all current partitions and creating a new partition table.

---

### Post by dkolars on 2022-04-08
> **oldfred said:**
> Please do not post screen shots or photos in line. Easy to add with Forum's advanced editor and paperclip icon.
[https://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098](https://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098)

You should only use FAT32 for smaller partitions. It cannot have a file over 4GB and has no journal making file recovery more difficult or impossible.

Windows formats will always show root as they do not support Linux ownership & permissions. Those are set only by how the partition is mounted.

How did you partition drive?
Post this, if still hdh:
sudo gdisk -l /dev/sdh
sudo fdisk -l

Partitioned with Gparted and Disks...

=========================
GPT fdisk (gdisk) version 1.0.5


Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: not present


***************************************************************
Found invalid GPT and valid MBR; converting MBR to GPT format
in memory. 
***************************************************************


Warning! Secondary partition table overlaps the last partition by
4 blocks!
Try reducing the partition table size by 16 entries.
(Use the 's' item on the experts' menu.)
Disk /dev/sdh: 2048000001 sectors, 7.6 TiB
Model: USB Disk        
Sector size (logical/physical): 4096/4096 bytes
Disk identifier (GUID): 162151F5-7CF0-4DDF-BBAD-E73AE121D24E
Partition table holds up to 128 entries
Main partition table begins at sector 2 and ends at sector 5
First usable sector is 6, last usable sector is 2047999995
Partitions will be aligned on 256-sector boundaries
Total free space is 250 sectors (1000.0 KiB)


Number  Start (sector)    End (sector)  Size       Code  Name
   1             256      2047999999   7.6 TiB     8300  Linux filesystem


===========================
Disk /dev/sdh: 7.64 TiB, 8388608004096 bytes, 2048000001 sectors
Disk model: USB Disk        
Units: sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x101ec8ed


Device     Boot Start        End    Sectors  Size Id Type
/dev/sdh1         256 2047999999 2047999744  7.6T 83 Linux


Disk /dev/mapper/luks-d3be1842-d1cf-4b4b-ab9b-d7489feb54ad: 7.64 TiB, 8388604854272 bytes, 2047999232 sectors
Units: sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

---

### Post by TheFu on 2022-04-08
So ... for an 8TB disk, you **MUST** use gpt to access over 2TB of storage. No other option.
It appears that someone put an MBR/MSDOS partition table on the SSD. That was a mistake.

Use **gparted** to create a new GUID partition table. This wipes the device and supports huge disks. Larger than any commercial disk available for the next 10+ yrs, to be certain.

Next, create a primary partition of whatever size you desire.
If also appears that LUKS encryption has been added to the disk. That will need to be recreated.  If this is an external disk, you can find "the bald nerd's" LUKS on USB how-to guide which will make using it more convenient on your system(s), while still having the expected protections when connected to other computers.

I would encourage creating a small - say 5G - partition that isn't encrypted to drop dumb files for easy transfers.  Probably make that NTFS.

These days, there is little reason to use FAT32 for anything except 1 exception - the EFI boot partition for a system.  If you want a small, flash drive with storage that can be accessed by almost any device, use exFAT.  If you have a small, flash drive that only needs to be accessed by Linux, use f2fs.  If you have larger storage and need to allow direct access (i.e. pulled into each of those OSes) by any OS, use NTFS. If you have larger storage that only needs to be accessed by Linux systems, use ext4 .... unless you have a specific reason to use something else.

GPT allows 128 primary partitions with basically unlimited sizes for each partition.  By choosing the correct file system, the file sizes can effectively be unlimited too.  NTFS and other MSFS file systems don't allow all characters in filenames (directories are just files too), while Unix/Linux file systems allow any characters to be used.

If you plan to allow storage to be access over a network by other systems from Linux, then choose a Linux native file system.  The other OSes won't see that. They only see the network storage protocol.

These are the choices to be made for data-only disks.

---

### Post by dkolars on 2022-04-09
> **TheFu said:**
> So ... for an 8TB disk, you **MUST** use gpt to access over 2TB of storage. No other option.
It appears that someone put an MBR/MSDOS partition table on the SSD. That was a mistake.

Use **gparted** to create a new GUID partition table. This wipes the device and supports huge disks. Larger than any commercial disk available for the next 10+ yrs, to be certain.

Next, create a primary partition of whatever size you desire.
If also appears that LUKS encryption has been added to the disk. That will need to be recreated.  If this is an external disk, you can find "the bald nerd's" LUKS on USB how-to guide which will make using it more convenient on your system(s), while still having the expected protections when connected to other computers.

I would encourage creating a small - say 5G - partition that isn't encrypted to drop dumb files for easy transfers.  Probably make that NTFS.

These days, there is little reason to use FAT32 for anything except 1 exception - the EFI boot partition for a system.  If you want a small, flash drive with storage that can be accessed by almost any device, use exFAT.  If you have a small, flash drive that only needs to be accessed by Linux, use f2fs.  If you have larger storage and need to allow direct access (i.e. pulled into each of those OSes) by any OS, use NTFS. If you have larger storage that only needs to be accessed by Linux systems, use ext4 .... unless you have a specific reason to use something else.

GPT allows 128 primary partitions with basically unlimited sizes for each partition.  By choosing the correct file system, the file sizes can effectively be unlimited too.  NTFS and other MSFS file systems don't allow all characters in filenames (directories are just files too), while Unix/Linux file systems allow any characters to be used.

If you plan to allow storage to be access over a network by other systems from Linux, then choose a Linux native file system.  The other OSes won't see that. They only see the network storage protocol.

These are the choices to be made for data-only disks.

THANK YOU!  That worked... did the gpt, formatted to ext4.  Then did chmod & chown, and now the user and group is me:me not root:root.  Copied files, played mp4's, deleted, re-did... all working fine!  Whew...  did not know about the gpt, knew about the size limits with all... made the difference!  

DK

---

### Post by dkolars on 2022-04-10
OK, I'm a-gonna "un-solve" this...  Copied a directory to SSD... tried to copy another directory... got this:

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=290268&stc=1[/IMG]

Any manipulation of the disk pops this up:

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=290269&stc=1[/IMG]

Looking at the disk in Gparted shows this:

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=290270&stc=1[/IMG]

According to Gparted, the drive has no files on it, but there are 2 directories with:

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=290271&stc=1[/IMG]

The warning is:

[INDENT]<i>Filesystem volume name:   SSD1[/INDENT]
[INDENT]Last mounted on:          <not available>[/INDENT]
[INDENT]Filesystem UUID:          c0c8474e-868f-4382-8969-beb9f2e537bf[/INDENT]
[INDENT]Filesystem magic number:  0xEF53[/INDENT]
[INDENT]Filesystem revision #:    1 (dynamic)[/INDENT]
[INDENT]Filesystem features:      has_journal ext_attr resize_inode dir_index filetype extent flex_bg sparse_super large_file huge_file dir_nlink extra_isize metadata_csum[/INDENT]
[INDENT]Filesystem flags:         signed_directory_hash [/INDENT]
[INDENT]Default mount options:    user_xattr acl[/INDENT]
[INDENT]Filesystem state:         clean[/INDENT]
[INDENT]Errors behavior:          Continue[/INDENT]
[INDENT]Filesystem OS type:       Linux[/INDENT]
[INDENT]Inode count:              256000000[/INDENT]
[INDENT]Block count:              2047999488[/INDENT]
[INDENT]Reserved block count:     102399974[/INDENT]
[INDENT]Free blocks:              2031588762[/INDENT]
[INDENT]Free inodes:              255999989[/INDENT]
[INDENT]First block:              0[/INDENT]
[INDENT]Block size:               4096[/INDENT]
[INDENT]Fragment size:            4096[/INDENT]
[INDENT]Reserved GDT blocks:      535[/INDENT]
[INDENT]Blocks per group:         32768[/INDENT]
[INDENT]Fragments per group:      32768[/INDENT]
[INDENT]Inodes per group:         4096[/INDENT]
[INDENT]Inode blocks per group:   256[/INDENT]
[INDENT]Flex block group size:    16[/INDENT]
[INDENT]Filesystem created:       Sat Apr  9 22:13:58 2022[/INDENT]
[INDENT]Last mount time:          n/a[/INDENT]
[INDENT]Last write time:          Sat Apr  9 22:14:33 2022[/INDENT]
[INDENT]Mount count:              0[/INDENT]
[INDENT]Maximum mount count:      -1[/INDENT]
[INDENT]Last checked:             Sat Apr  9 22:13:58 2022[/INDENT]
[INDENT]Check interval:           0 (<none>)[/INDENT]
[INDENT]Lifetime writes:          18 MB[/INDENT]
[INDENT]Reserved blocks uid:      0 (user root)[/INDENT]
[INDENT]Reserved blocks gid:      0 (group root)[/INDENT]
[INDENT]First inode:              11[/INDENT]
[INDENT]Inode size:	          256[/INDENT]
[INDENT]Required extra isize:     32[/INDENT]
[INDENT]Desired extra isize:      32[/INDENT]
[INDENT]Journal inode:            8[/INDENT]
[INDENT]Default directory hash:   half_md4[/INDENT]
[INDENT]Directory Hash Seed:      7fad8eb0-b9ac-4f53-b223-5b1052bcf9c3[/INDENT]
[INDENT]Journal backup:           inode blocks[/INDENT]
[INDENT]Checksum type:            crc32c[/INDENT]
[INDENT]Checksum:                 0xca282ca4</i>[/INDENT]
[INDENT]
[/INDENT]
[INDENT]<i>dumpe2fs 1.45.5 (07-Jan-2020)[/INDENT]
[INDENT]dumpe2fs: Corrupt extent header while reading journal super block</i>[/INDENT]
[INDENT]
[/INDENT]
[INDENT]<i>Unable to read the contents of this file system![/INDENT]
[INDENT]Because of this some operations may be unavailable.[/INDENT]
[INDENT]The cause might be a missing software package.[/INDENT]
[INDENT]The following list of software packages is required for ext4 file system support:  e2fsprogs v1.41+.</i>
[/INDENT]

I have other drives that are formatted to ext4, and they work just fine, and e2fsprogs is installed.  WTH?

Looking at things with Disks, it shows that SSD1 is not mounted, and when I click to mount, get error message that it can't be mounted.  Again, WTH?

---

### Post by TheFu on 2022-04-10
Don't trust Gnome-Disks.
Please don't post huge images inline.  Use the 'attach' option in the advanced editor, iffffff an image is needed.

However, let's dump the GUI stuff for now.  Please run these commands and post the exact command/output back here wrapped in 'code' tags.  Mount the storage first.  Use the **mount** command (with appropriate options) to make that happen.

```
df -hT -x squashfs -x tmpfs -x devtmpfs
lsblk -e 7 -o name,size,type,fstype,mountpoint
du -hsc  /place/you/mounted/it  | sort -h
ls -al  /place/you/mounted/it
```

Feel free to edit any filenames, if privacy is a worry. I would.  But don't touch anything else please.
I've used 'code' forum tags above, so if you don't see exactly that wrapper in what you post, please fix it. Too hard to read the output when columns aren't maintained.

There should be at least 1 error in the **du** output.  If not, that's a problem too. Here's an example:
```
du: cannot read directory '/d/D1/lost+found': Permission denied
```

If any 'loop' storage gets included, please remove those lines. The options above should prevent that, but ... 

Anyway, those commands will tell us all sorts of things about the situation.

---

### Post by oldfred on 2022-04-10
Post what TheFu has asked for.
But the fix is often just to use gdisk and write an update.

If you have data you want to keep, always do a backup first.
And best to backup partition table entries, so if changes not correct you can revert to current partitions.

New sfdisk that supports gpt will also work for backup of partition table entries:
sfdisk -d /dev/sdX > sdX.bkp  # change to your drive like /dev/sdg or /dev/nvme0n1

repair gpt:
[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)
More repair info  use p, v & w to write the partition table. If not correct just use q to quit. :

---

### Post by dkolars on 2022-04-10
> **TheFu said:**
> Don't trust Gnome-Disks.
Please don't post huge images inline.  Use the 'attach' option in the advanced editor, iffffff an image is needed.

However, let's dump the GUI stuff for now.  Please run these commands and post the exact command/output back here wrapped in 'code' tags.  Mount the storage first.  Use the **mount** command (with appropriate options) to make that happen.

```
df -hT -x squashfs -x tmpfs -x devtmpfs
lsblk -e 7 -o name,size,type,fstype,mountpoint
du -hsc  /place/you/mounted/it  | sort -h
ls -al  /place/you/mounted/it
```

Feel free to edit any filenames, if privacy is a worry. I would.  But don't touch anything else please.
I've used 'code' forum tags above, so if you don't see exactly that wrapper in what you post, please fix it. Too hard to read the output when columns aren't maintained.

There should be at least 1 error in the **du** output.  If not, that's a problem too. Here's an example:
```
du: cannot read directory '/d/D1/lost+found': Permission denied
```

If any 'loop' storage gets included, please remove those lines. The options above should prevent that, but ... 

Anyway, those commands will tell us all sorts of things about the situation.

Sorry about the pics... was told to use paperclip after 1st post in this thread.  So, I did.  hmmm?  My option is to Insert Inline, so I did.

OK, #1, I cannot mount this drive when formatted to ext4.  Messed around with gdisk commands... nope, nothing will work to repair the Backup GPT...  zapped the disk, created new partition, formatted to ext4, nope, not mountable...

Some errors:
```
sudo gdisk /dev/sdhGPT fdisk (gdisk) version 1.0.5

Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: not present

***************************************************************
Found invalid GPT and valid MBR; converting MBR to GPT format
in memory. THIS OPERATION IS POTENTIALLY DESTRUCTIVE! Exit by
typing 'q' if you don't want to convert your MBR partitions
to GPT format!
***************************************************************
Warning! Secondary partition table overlaps the last partition by 4 blocks!
Try reducing the partition table size by 16 entries.
(Use the 's' item on the experts' menu.)

```

```

sudo hdparm -I /dev/sdh

/dev/sdh:
SG_IO: bad/missing sense data, sb[]:  70 00 05 00 00 00 00 0a 00 00 00 00 24 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00

ATA device, with non-removable media
Standards:
    Likely used: 1
Configuration:
    Logical        max    current
    cylinders    0    0
    heads        0    0
    sectors/track    0    0
    --
    Logical/Physical Sector size:           512 bytes
    device size with M = 1024*1024:           0 MBytes
    device size with M = 1000*1000:           0 MBytes 
    cache/buffer size  = unknown
Capabilities:
    IORDY not likely
    Cannot perform double-word IO
    R/W multiple sector transfer: not supported
    DMA: not supported
    PIO: pio0 

```

```
Unable to read the contents of this file system!Because of this some operations may be unavailable.
The cause might be a missing software package.
The following list of software packages is required for ext4 file system support:  e2fsprogs v1.41+
```

So, I think I have a cheap tiny drive that's heading to the recycling bin.

---

### Post by oldfred on 2022-04-10
Is it really MBR or gpt?

If gpt:
last partition overlaps backup partition table
[http://ubuntuforums.org/showthread.php?t=1956173](http://ubuntuforums.org/showthread.php?t=1956173)
Check start & end, delete and recreate without overlap. Backup vital just in case.

---

### Post by TheFu on 2022-04-10
SO .... you decided to run 2 commands that weren't asked for
AND
not run the requested commands?

---

### Post by dkolars on 2022-04-11
> **TheFu said:**
> SO .... you decided to run 2 commands that weren't asked for
AND not run the requested commands?


In an earlier reply you said:  > [COLOR=#000000]However, let's dump the GUI stuff for now. Please run these commands and post the exact command/output back here wrapped in 'code' tags. Mount the storage first. Use the **mount** command (with appropriate options) to make that happen.[/COLOR]

"Mount the storage first." --  In my response to that I said that I can not mount the drive.  I would have gladly run the commands you suggested had I been able to mount the drive!

I will be contacting seller to see about returning the drive.  Enough of this madness -- taking too much of my time... the ride is not worth the fare, I have many other more important things to do.  I sometimes yearn for the old days:  format E: 'poof', done.

---

### Post by TheFu on 2022-04-11
Boot from a _try ubuntu_ flash drive.
BTW, not all the commands require the disk to be mounted, just connected.

---

### Post by dkolars on 2022-04-11
> **TheFu said:**
> SO .... you decided to run 2 commands that weren't asked for
AND not run the requested commands?

Here's the results for the commands (1st one not applicable, as disk not mounted) -- Haven't had time for any more "things"...

> **lsblk -e 7 -o name,size,type,fstype,mountpoint**NAME     SIZE TYPE FSTYPE MOUNTPOINT
sdh      7.6T disk        
&#9492;&#9472;sdh1   7.6T part ext4   
sr0     1024M rom
====================================
**du -hsc  /dev/sdh  | sort -h**
0	/dev/sdh
0	total
====================================
**ls -al /dev/sdh**
brw-rw---- 1 root disk 8, 112 Apr 11 11:15 /dev/sdh

---

