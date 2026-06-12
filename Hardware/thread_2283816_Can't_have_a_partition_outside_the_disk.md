---
title: "Can't have a partition outside the disk"
date: 2015-06-24
forum: Hardware
---

### Post by steve206 on 2015-06-24
Hello, I have tried to fix this myself with fixparts and by reading other posts but I really don't know what the problem is with my situation so I am asking for help. Gparted reports a disk (sda) as unallocated. It is a 1GB Samsung disk holding data, mainly movies and music with NTFS. The problem arose when I accidentally deleted a partition and then restored it with testdisk. I can still read all the data on the disk without any problems but I don't like errors being reported by gparted.
If I try "sudo fdisk -l", then sda is not listed. It simply states the same info from gparted-"Error: Can't have a partition outside the disk". All the other disks are listed properly. Fixparts identifies an oversized partition and wants to delete it . I press "w" for write but the problem is not fixed. I am using Ubuntu 14.04. Any suggestions?

---

### Post by weatherman2 on 2015-06-24
My suggestion is to copy all your data off of this disk to another location, then wipe the disk and re-format it and start over - and feel grateful you were able to get all your data off.

---

### Post by steve206 on 2015-06-24
Yes, luckily I can always do that.....so far. I thought I'd check to see if there was some way to shift/reduce the partition and still keep the data.

---

### Post by oldfred on 2015-06-24
Post this:
sudo parted -l

Is drive partitioned with MBR(msdos) or gpt(GUID)?
Above should show that.

Sometimes you can just use fdisk with MBR and write partition table. Or sfdisk and manually edit partition details.
Bit more difficult with gpt, but gpt does not normally have as many issues.

---

### Post by steve206 on 2015-06-24
Hi Oldfred,
It's an msdos partition. sudo parted -l doesn't report the affected drive. Here's the output:

Error: Cannot have a partition outside the disk!                          


Model: ATA WDC WD10EZEX-00B (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos



Number  Start   End     Size   Type     File system  Flags
 1      1049kB  241GB   241GB  primary  ntfs         boot
 2      241GB   1000GB  759GB  primary  ntfs




Model: ATA Corsair Force LS (scsi)
Disk /dev/sdc: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End    Size    Type      File system  Flags
 1      32.3kB  114GB  114GB   primary   ext4         boot
 2      114GB   120GB  6482MB  extended

I'm transferring data from sda to an external disk to be on the safe side.

---

### Post by oldfred on 2015-06-25
I am surprised you can mount it to copy data if parted will not show any partitions. But then backup is the best choice.

Some other info:
 sfdisk to fix extended beyond end -partition outside the disk!
[http://ubuntuforums.org/showthread.php?t=1012825](http://ubuntuforums.org/showthread.php?t=1012825)
[http://gparted.org/h2-fix-msdos-pt.php#partition-outside-disk](http://gparted.org/h2-fix-msdos-pt.php#partition-outside-disk)

---

### Post by steve206 on 2015-06-25
Thanks mate. I actually went through some old threads of yours to try and fix this. I had a quick look at that first thread and there is a suggestion there to use testdisk again. What I'll do is transfer my data and then see if testdisk can help. The other link you gave me is one I have already been through. It led me to fixparts but the solution didn't work. Anyway, with the data safe I should be ok now. It will just be for interest sake to see if I can repair the partition. I'll come back and close the thread later.

---

### Post by steve206 on 2015-06-25
Naaaa. In the end I just moved the data and re-partitoned the drive. All good now.

---

