---
title: "how to shrink superblock for ext3, after filesystem successfully shrank?"
date: 2011-08-08
forum: Hardware
---

### Post by tlroche on 2011-08-08
**summary:** I've got a box running ubuntu lucid (otherwise up-to-date) with a single internal HD with all (non-swap) filesystems on ext3. I'm attempting to grow partitions at the beginning and middle of the HD, hence first want to shrink the partition at the end of the HD and move its filesystem to the right. GParted shrank the filesystem, but not its superblock. How to fix?

**details:**

```
$ lsb_release -ds
> Ubuntu 10.04.3 LTS
$ uname -rv
> 2.6.32-33-generic #71-Ubuntu SMP Wed Jul 20 17:27:30 UTC 2011
```

This laptop (running ubuntu lucid) has a single internal HD:

```
$ sudo fdisk -l -u
> Disk /dev/sda: 250.1 GB, 250059350016 bytes
> 255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
> Units = sectors of 1 * 512 = 512 bytes
> Sector size (logical/physical): 512 bytes / 512 bytes
> I/O size (minimum/optimal): 512 bytes / 512 bytes
> Disk identifier: 0x0009c48f

Its partitions are
/dev/sda1  /
/dev/sda5  swap
/dev/sda6  /home

>    Device Boot      Start         End      Blocks   Id  System
> /dev/sda1   *           1    29296875    14648437+  83  Linux
> /dev/sda2        29296876   488397167   229550146    5  Extended
> /dev/sda5        29296877    36837890     3770507   82  Linux swap / Solaris
> /dev/sda6        36837892   475808627   219485368   83  Linux
$ sudo parted /dev/sda unit s print
> Model: ATA ST9250410AS (scsi)
> Disk /dev/sda: 488397168s
> Sector size (logical/physical): 512B/512B
> Partition Table: msdos
>
> Number  Start      End         Size        Type      File system     Flags
>  1      1s         29296875s   29296875s   primary   ext3            boot
>  2      29296876s  488397167s  459100292s  extended
>  5      29296877s  36837890s   7541014s    logical   linux-swap(v1)
>  6      36837892s  475808627s  438970736s  logical   ext3
```

The swap partition (/dev/sda5) is too small, and the root partition (/dev/sda1) could also use more free space, so my plan is to perform the following actions in GParted:

[LIST=1]
[*]Move /dev/sda6 [home] to the right and shrink it. This should produce unallocated space between /dev/sda5 and /dev/sda6.
[*]Move /dev/sda5 [swap] to the right and grow it. This should consume some of the unallocated space, placing the remainder at the beginning of /dev/sda5, which is at the beginning of /dev/sda2.
[*]Move /dev/sda2 [extended] to the right and shrink it. This should produce unallocated space between /dev/sda1 and /dev/sda2.
[*]Grow /dev/sda1 [root]. This should consume the unallocated space between /dev/sda1 and /dev/sda2.
[/LIST]

Unfortunately, in my first attempt to do step=1, GParted abended with an error after shrinking partition=/dev/sda6 and attempting to move its filesystem. I did not record the error, but noted it was from e2fsck.

I restarted the box from its HD. Things looked normal (famous last words :-) so I retried step=1 with GParted. The values in the UI were nearly the same, except that most had changed by ± 1 MiB, but, on hitting button=Apply, I got nearly the same error, which I recorded:

```
> GParted 0.9.0
> Libparted 2.3

> Move /dev/sda6 to the right and shrink it from 209.32 GiB to 209.32 GiB  00:00:01    ( ERROR )

> calibrate /dev/sda6  00:00:00    ( SUCCESS )

> path: /dev/sda6
> start: 36837892
> end: 475808627
> size: 438970736 (209.32 GiB)
```

The physical size=54871342 looks correct, so I'm guessing GParted correctly resized the partition, but then was unable to write the superblock. The bad news is, neither can I. The good news is, the filesystem appears to be otherwise OK, except that when I reboot to lucid (i.e., on the internal HD), before login I get

```
Errors were found while checking the disk drive for /home
F to attempt to fix the errors, I to ignore, S to skip mounting or M for manual recovery
```

But I can then login, and everything appears to work (particularly, /home automounts). While mounted in lucid, for the helluvit, I tried

```
me@it:~$ sudo resize2fs -f /dev/sda6
> resize2fs 1.41.11 (14-Mar-2010)
> Filesystem at /dev/sda6 is mounted on /home; on-line resizing required
> On-line shrinking from 54871597 to 54871342 not supported.
```

So I rebooted the liveCD and ran

```
user@debian:~$ sudo resize2fs -f /dev/sda6
> resize2fs 1.42-WIP (02-Jul-2011)
> Resizing the filesystem on /dev/sda6 to 54871342 (4k) blocks.
> resize2fs: Attempt to read block from filesystem resulted in short read while trying to resize /dev/sda6
> Please run 'e2fsck -fy /dev/sda6' to fix the filesystem
> after the aborted resize operation.
user@debian:~$ sudo e2fsck -fy /dev/sda6
> e2fsck 1.42-WIP (02-Jul-2011)
> The filesystem size (according to the superblock) is 54871597 blocks
> The physical size of the device is 54871342 blocks
> Either the superblock or the partition table is likely to be corrupt!
> Abort? yes
```

So `resize2fs` and `e2fsck` are not playing well together. I'm wondering:

[LIST=1]
[*]How to fix /dev/sda6? Particularly, its superblock.
[*]How to move the filesystem on /dev/sda6 to the right, so as to proceed with my plan (above)? Though I'm hoping GParted will do this, if I can fix the superblock on /dev/sda6 ...
[/LIST]

---

### Post by tlroche on 2011-08-08
> **tlroche said:**
> [LIST=1]
[*]How to fix /dev/sda6? Particularly, its superblock.
[*]How to move the filesystem on /dev/sda6 to the right, so as to proceed with my plan (above)? Though I'm hoping GParted will do this, if I can fix the superblock on /dev/sda6 ...
[/LIST]

The good news is, I have a fix for the first problem. The bad news is, not the second :-( But for the problem with the primary superblock, the solution was, use a backup superblock. I stumbled upon the backup superblocks doing

```
$ sudo dumpe2fs /dev/sda6 | fgrep -e 'Block size'
> dumpe2fs 1.41.11 (14-Mar-2010)
> Block size:               4096
$ sudo dumpe2fs /dev/sda6 | fgrep -ie 'superblock' | wc -l
> dumpe2fs 1.41.11 (14-Mar-2010)
> 15
$ sudo dumpe2fs /dev/sda6 | fgrep -ie 'superblock'
> dumpe2fs 1.41.11 (14-Mar-2010)
>   Primary superblock at 0, Group descriptors at 1-14
>   Backup superblock at 32768, Group descriptors at 32769-32782
...
```

`info e2fsck` shows how to use the backup superblocks:

```
OPTIONS
...
-b superblock

   Instead of using the normal superblock, use an alternative
   superblock specified by superblock. This option is normally used
   when the primary superblock has been corrupted. The location of
   the backup superblock is dependent on the filesystem's blocksize.
```

So I booted gparted-live-0.9.0-7 again and did

```
user@debian:~$ sudo e2fsck -b 32768 -fvy /dev/sda6
> e2fsck 1.42-WIP (02-Jul-2011)
> Pass 1: Checking inodes, blocks, and sizes
> Pass 2: Checking directory structure
> Pass 3: Checking directory connectivity
> Pass 4: Checking reference counts
> Pass 5: Checking group summary information
> Free blocks count wrong for group #1 (26596, counted=26645).
> Fix? yes
```

... 99 more "Free blocks count wrong" omitted

```
> Directories count wrong for group #1565 (27, counted=26).
> Fix? yes

> Free inodes count wrong for group #1571 (16381, counted=16383).
> Fix? yes

> Free inodes count wrong (27023121, counted=27023056).
> Fix? yes
```

but that was the extent of the disk's problem, other than bad primary superblock. Note no bad blocks! Also subsequent runs of `e2fsck` *without* the '-b' run normally, so I'm guessing running `e2fsck -b' fixed the primary superblock.

Unfortunately solving this problem [did not help GParted much](http://ubuntuforums.org/showthread.php?p=11132542), but at least I get to mark this thread "solved" :-) and hopefully it will be useful to OP.

---

