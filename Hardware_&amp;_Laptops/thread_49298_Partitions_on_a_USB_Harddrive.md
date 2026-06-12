---
title: "Partitions on a USB Harddrive"
date: 2005-07-15
forum: Hardware &amp; Laptops
---

### Post by Sephiriz on 2005-07-15
I recently acquired a 250 gigabyte capacity harddrive that hooks up to the computer via either USB or Firewire.  I took all of my songs and moved them onto there, and did this while using Windows XP.  The file system is NTFS, and there seem to be a bunch of partitions already:

```

     Device Boot      Start         End      Blocks   Id  System
/dev/sda1p1   ?       13578      119522   850995205   72  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda1p2   ?       45382       79243   271987362   74  Unknown
Partition 2 does not end on cylinder boundary.
/dev/sda1p3   ?       10499       10499           0   65  Novell Netware 386
Partition 3 does not end on cylinder boundary.
/dev/sda1p4          167628      167631       25817+   0  Empty
Partition 4 does not end on cylinder boundary.

``` 

In any case, I was hoping to have the harddrive running on a filesystem that would make it fully readable and writable in both Linux and Windows, and I want to somehow preserve the songs if possible without having to resort to other removable storage means like a CD, since that, quite simply, will be a pain.

So, can anyone help me out with some advice as to how I will go about with this?  I have about 2000 songs totaling to 9.1 gigs, which means I can't move it to my linux harddrive since thats only 20 gigs and I've already used up 12.

---

### Post by Kyral on 2005-07-15
I dunno, but it maybe Rescue software or somehting on it. I know Maxtor OneTouch drives do the same thing. I would just wipe them out with fdisk and make one big FAT32 partition

---

### Post by Sephiriz on 2005-07-15
So the first partition is the one that consists of all the music?

Also, is FAT32 fully compatible in both Linux and Windows environments?

---

### Post by evilghost on 2005-07-15
Did you "fdisk /dev/sda" or "fdisk /dev/sda1".  I had a similiar experience with multiple paritions when I made a typo/stupid mistake.  I think you'll want to print the partition table on /dev/sda not /dev/sda1 and it may make more sense, if that is what you did.

---

### Post by Sephiriz on 2005-07-16
Oh that definitely did the trick there, thanks.

```

Disk /dev/sda: 250.0 GB, 250059350528 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30401   244196001    7  HPFS/NTFS


``` 

I assume its possible to make a massive partition of all the unused area on this harddrive, turn it into FAT32 (which I hope is compatible in both WinXP and Linux), and then transfer the songs somehow?  Though I'm still not sure how I would access the different partitions, do you mount each partition individually?

I'm sorry, I'm very new to the whole Linux scene, and am deathly afraid of losing all my files by not knowing exactly what I'm doing.

---

### Post by evilghost on 2005-07-16
Hey, no problem.  I just had to take this route myself.

Ideally, you want to convert your NTFS partition to FAT32.  However, realize this.  Fat32 supports a max filesize of 4GB, while NTFS supports greater filesizes (I can't remember the value, but it's pretty high).  If you have any files greater than 4GB, they may truncate on move.

What I did was create a temporary directory and "cp -a" the files over.

Then, I fdisk'd, deleted the partition, created a new one, hit "t" then "l" and changed it to Fat32.  "w" to write the changes and did a mkfs -t vfat /dev/sda1 to format it.  I rebooted so it'd auto-mount and copyied the files back over.

You don't need to reparition your primary disk, you can move ntfs files over to ext3, and then repartition/format your USB drive to fat32, and move them from ext3 to fat32.

The deal is Linux can read NTFS, but it's unsafe to write to it.  Converting to Fat32 will enable interoperability between Windows and Linux, just keep in mind the 4GB limit (no single file can exceed 4GB)

---

### Post by Sephiriz on 2005-07-16
Thank you very much.  The 4G limit doesn't bother me much, seeing as I'm not making massive raw log files or anything.  Once again, many thanks.

---

### Post by evilghost on 2005-07-16
No problem at all, glad I could help ;)

I recently was banging my head against the wall trying to figure out why my local backups would truncate exactly at 4GB when backing up to my FAT32 firewire drive.  I soon learned that it was a limitation of the filesystem, not the actual tar application like I was accustomed to in the past, with things like wget and tar kernel limitations.

---

### Post by Sephiriz on 2005-07-16
EDIT:  Nevermind, I got it!  I forgot to do what was advised, namely that command to format the partition.

Bah for whatever strange reason, the changes refuse to write to the drive.  I already make sure the drive is unmounted before I proceed, and then when I attempt to write the the new table, I get this error, the drive automatically remounts, and nothing has changes.

This is the precise error I get when attempting to use fdisk:

```

Calling ioctl() to re-read partition table.

WARNING: Re-reading the partition table failed with error 16: Device or resource busy.
The kernel still uses the old table.
The new table will be used at the next reboot.

WARNING: If you have created or modified any DOS 6.x
partitions, please see the fdisk manual page for additional
information.
Syncing disks.

```

When I reboot, nothing is changed, at all.  Help is appreciated.

---

### Post by evilghost on 2005-07-16
So you're good, and everythings working? :)

---

### Post by Sephiriz on 2005-07-16
Yep, although I'm just curious as to why the maximum-sized partition is only like 82% of the entire harddrive.  Is there a limit to partition size?  Just curious, its not really a problem.

Once again, many thanks.  Heaps of thanks!   \\:D/

---

### Post by evilghost on 2005-07-16
Hmmm...did you do FAT32 LBA?  This is how mine is setup, and I'm showing full partition size:

```

Disk /dev/sda: 80.0 GB, 80026361856 bytes
240 heads, 63 sectors/track, 10337 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       10337    78147688+   c  W95 FAT32 (LBA)

```

No problem on the help, I know I'm running Linux because I'm sick of Microsoft's shovelware and enjoy the community based effort. ;)

---

### Post by Sephiriz on 2005-07-17
Well I'm not quite sure what the difference between the W95 FAT32 (LBA) and the W95 FAT32 is, but here is my setup:

```

Disk /dev/sda: 250.0 GB, 250059350528 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30401   244196001    b  W95 FAT32


```

As I said, its not a very big deal.  I noticed this seeming partition limit when I quickly jumped into Windows and tried out Partition Magic, it would only allow the partition to go to a certain size.  Possibly FAT32 has this limit?  I'm not sure, I was only introduced to the concept of a partition like, 3 weeks ago  :-P

---

### Post by ifishfortorque on 2005-07-18
For some reason, Windows XP won't cooperate with a FAT32 partition greater than about 32 gigs in size.  For example, I had 60 GB for data on my hard drive; I had to split it 30 and 30, then format it FAT32, and then Windows had no problem with it.

---

### Post by Sephiriz on 2005-07-18
Well my partition size is roughly 240ish (can't check right now, at another comp) gigs in size, so maybe FAT32 somehow operates on a percentage?  How wonderfully arcane this all seems to be, eh?

---

