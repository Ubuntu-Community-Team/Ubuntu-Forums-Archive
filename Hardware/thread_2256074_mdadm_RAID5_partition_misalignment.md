---
title: "mdadm RAID5 partition misalignment"
date: 2014-12-09
forum: Hardware
---

### Post by canoemoose on 2014-12-09
Hi all,

First, some background:
I've got a box which previously contained 4no 1.5TB drives in RAID5 (with a separate boot/OS drive) which I set up with no problems at all back in 2010.  2 of these drives recently failed at the same time, and so given that I'd already lost my data I'm taking the opportunity to increase the size of the array by using 4no 2TB drives, also in RAID5.

My problem:
However, when I create the array from within Disk Utility (File > Create > RAID array..., select the 4 empty disks) as I did back in 2010, I end up with a Disk Utility warning for each drive in the array:> The partition is misaligned by 512 bytes.  This may result in very poor performance.  Repartitioning is suggested.

As far as I have been able to work out from reading around, this is due to my new drives having 4096B physical sectors as reported by fdisk:
```
root@kermit:/home/moosey# fdisk -l /dev/sd[bcde]

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000da73f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      243201  1953512001   fd  Linux RAID autodetect
Partition 1 does not start on physical sector boundary.

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00060525

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      243201  1953512001   fd  Linux RAID autodetect
Partition 1 does not start on physical sector boundary.

Disk /dev/sdd: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000e82ec

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      243201  1953512001   fd  Linux RAID autodetect
Partition 1 does not start on physical sector boundary.

Disk /dev/sde: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0006e913

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1      243201  1953512001   fd  Linux RAID autodetect
Partition 1 does not start on physical sector boundary. 
```

Fixing this in the instance of a "normal" non-RAIDed HDD seems to be as simple as deleting/recreating the offending partition with a start position which is a multiple of 4 sectors, to ensure the logical/physical block sizes line up.

However, in the workflow I've described above, at no point am I asked whether or by how much to offset the partition that Disk Utility automatically creates for use in the RAID, and I'm not seemingly able to manually create a partition to use for the RAID - if I attempt to do so, Disk Utility just says the drive has no free space.

How do I get around this?

I'm not afraid of the command line, I'm only using Disk Utility because it's there...
As always, if you need more info then just let me know.

As an aside, what would you recommend as a filesystem for this 6TB share? It's going to be used to store backups as a mixture of large proprietary compressed images from Windows machines and also rsync'd files/folders from other network shares - mainly photos/music.  I used EXT4 last time but wondered if XFS would be better and seeing as I've got the chance to change wondered what's best...

The machine is the server in my sig, but the sig's a little out of date... If you're reading this before I update it, it's a 2.7GHz Athlon 64, 2GB RAM, 80GB boot/OS drive, 4no 2TB in RAID5 for backups, 2no 1.5TB LVM'd together for network shares.  Running 10.04 desktop, kernel 2.6.32-64-generic with latest updates as well as manually-applied security fixes. Upgrading to a more current LTS will happen at some point, honest...

---

### Post by weatherman2 on 2014-12-09
If you create a partition with a modern version of Gparted, it will automatically align it to a 2048 byte boundary.  If you are using an old (2010?) version of Ubuntu its version of partition creation tools will probably not do that automatically.  It's not recommended to use an old version of Ubuntu (if that's what you are doing) - but if you are, you can always create the partitions with a newer Ubuntu boot disk so they will automatically get aligned.

You don't have to create the RAID with your current OS installation, either.  Look up a guide for creating the array, and you can do it with a newer version of Ubuntu if need be, then import into the current version of Ubuntu you are using.

---

### Post by canoemoose on 2014-12-09
Yeah, I'd tried manually creating correctly-aligned partitions before - whilst I could create them in the right places (in Gparted/fdisk), Disk Utility would then refuse to use them for the RAID - it'd just say the drive had no free space.  Am I missing something when creating these partitions?

---

### Post by weatherman2 on 2014-12-09
Have you tried adding a "raid" flag to your new partition?  in Gparted, after you've created the partition, right-click on the partition and choose "Manage Flags" then check the "raid" box.

Or try setting it in the terminal using parted directly:

[https://plone.lucidsolutions.co.nz/linux/io/using-parted-to-create-a-raid-primary-partition](https://plone.lucidsolutions.co.nz/linux/io/using-parted-to-create-a-raid-primary-partition)

---

### Post by canoemoose on 2014-12-10
Right.  I couldn't remember exactly how much of that I'd actually tried, so had another go.  Disk Utility still refused to use the new partitions, but doing it the manual way with mdadm in the terminal seems to have worked.  This is what I did:

For each of /dev/sd[bcde] in turn:

```
root@kermit:/home/moosey# fdisk -cu /dev/sde

The device presents a logical sector size that is smaller than
the physical sector size. Aligning to a physical sector (or optimal
I/O) size boundary is recommended, or performance may be impacted.

Command (m for help): p

Disk /dev/sde: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0006e913

   Device Boot      Start         End      Blocks   Id  System

Command (m for help): n
Command action
   e   extended
   p   primary partition (1-4)
p
Partition number (1-4): 1
First sector (2048-3907029167, default 2048): 
Using default value 2048
Last sector, +sectors or +size{K,M,G} (2048-3907029167, default 3907029167): 
Using default value 3907029167

Command (m for help): t
Selected partition 1
Hex code (type L to list codes): fd
Changed system type of partition 1 to fd (Linux RAID autodetect)

Command (m for help): p

Disk /dev/sde: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0006e913

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1            2048  3907029167  1953513560   fd  Linux RAID autodetect

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.
Syncing disks.
```

This fdisk -l then reports as follows:

```
root@kermit:/home/moosey# fdisk -l /dev/sd[bcde]

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
81 heads, 63 sectors/track, 765633 cylinders
Units = cylinders of 5103 * 512 = 2612736 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000da73f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      765634  1953513560   fd  Linux RAID autodetect

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
81 heads, 63 sectors/track, 765633 cylinders
Units = cylinders of 5103 * 512 = 2612736 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00060525

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      765634  1953513560   fd  Linux RAID autodetect

Disk /dev/sdd: 2000.4 GB, 2000398934016 bytes
81 heads, 63 sectors/track, 765633 cylinders
Units = cylinders of 5103 * 512 = 2612736 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000e82ec

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      765634  1953513560   fd  Linux RAID autodetect

Disk /dev/sde: 2000.4 GB, 2000398934016 bytes
81 heads, 63 sectors/track, 765633 cylinders
Units = cylinders of 5103 * 512 = 2612736 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0006e913

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1      765634  1953513560   fd  Linux RAID autodetect
```

I then went on to create the array:

```
root@kermit:/home/moosey# mdadm --create --verbose /dev/md0 --level=5 --chunk=1024 --raid-devices=4 /dev/sd[bcde]1
mdadm: layout defaults to left-symmetric
mdadm: size set to 1953513472K
mdadm: array /dev/md0 started.
```

which /proc/mdstat says is recovering as I type:
```
root@kermit:/home/moosey# cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sde1[4] sdd1[2] sdc1[1] sdb1[0]
      5860540416 blocks level 5, 1024k chunk, algorithm 2 [4/3] [UUU_]
      [>....................]  recovery =  1.6% (32060928/1953513472) finish=502.3min speed=63748K/sec
      
unused devices: <none>
```

Can you see anything wrong with this before I give it a filesystem and start putting data on it?

Also, any opinions on ext4 vs xfs?

Thanks very much for your help so far - I guess the lesson learned is that sometimes the graphical tools are too clever for their own good - trying to stop me using a disk that could have other data on it - and that the manual way is always going to work...

---

### Post by weatherman2 on 2014-12-10
Your fdisk -l output still shows all of the partitions starting at sector 1 (misaligned) and not a multiple of 8, which is what you need to be correctly aligned.  Your output should look something like this:

```

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
81 heads, 63 sectors/track, 765633 cylinders
Units = cylinders of 5103 * 512 = 2612736 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000da73f


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048      765634  1953513560   fd  Linux RAID autodetect

```

Where the Start is 2048 not 1.  As I said a few posts ago, newer versions of tools like Gparted automatically create aligned partitions, so if you are using an older version of Ubuntu, try creating the new partitions with say a live boot disk of a newer Ubuntu.

---

### Post by weatherman2 on 2014-12-10
I have always used ext4 in recent years and had no issues with it.  I don't have any experience with xfs.

---

### Post by canoemoose on 2014-12-10
Actually, that's my error above - I forgot to pass -u to fdisk -l to make it display its output using sectors as the unit.  With that included I get the following:

```
root@kermit:/home/moosey# fdisk -ul /dev/sd[bcde]

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
81 heads, 63 sectors/track, 765633 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000da73f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  3907029167  1953513560   fd  Linux RAID autodetect

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
81 heads, 63 sectors/track, 765633 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00060525

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048  3907029167  1953513560   fd  Linux RAID autodetect

Disk /dev/sdd: 2000.4 GB, 2000398934016 bytes
81 heads, 63 sectors/track, 765633 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000e82ec

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1            2048  3907029167  1953513560   fd  Linux RAID autodetect

Disk /dev/sde: 2000.4 GB, 2000398934016 bytes
81 heads, 63 sectors/track, 765633 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0006e913

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1            2048  3907029167  1953513560   fd  Linux RAID autodetect
```

So I think I'm all good.

I'll stick with ext4 I think, from reading about I'm unlikely to gain any performance increases with xfs in my setup...

Thanks for your help!

---

### Post by weatherman2 on 2014-12-10
Sounds good!

---

