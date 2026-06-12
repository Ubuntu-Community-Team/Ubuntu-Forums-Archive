---
title: "Ubuntu-created FAT32 Partition not showing in Windows"
date: 2005-12-16
forum: Installation &amp; Upgrades
---

### Post by 117 on 2005-12-16
Hi guys, been having a little dabble with Ubuntu for a month or 2 and now really into it, but I have a partitioning problem.

I freshly installed Ubuntu the other day, beforehand I booted to a live cd and used gparted to partition my hard-drive as such:

Partition 1 - NTFS - 75Gb (my XP Pro install)
Partition 2 - FAT32 - 60Gb (for sharing media between Windows/Linux)
Partition 3 - ext3 - 65Gb (my Ubuntu / install)
Partition 5 - ext3 - 60Gb (my Ubuntu /home install)
Partition 6 - swap - 2Gb (my swap partition)

there's no Partition 4 for some reason?

From reading other threads I found that I needed to edit /etc/fstab , which i did as follows:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       /home           ext3    defaults        0       2
# /dev/sda1       /media/sda1     ntfs    defaults        0       0
# /dev/sda2       /media/sda2     vfat    defaults        0       0
/dev/sda6       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/sda1 /media/sda1 ntfs nls=utf8,umask=0222 0 0
/dev/sda2 /media/sda2 vfat iocharset=utf8,umask=000 0 0
```

now, when I boot to Ubuntu, I get a warning about utf8 charset being dangerous for FAT32 file-systems, but I can read and write to the FAT32 partition fine, and read the NTFS partition fine in Ubuntu.

When I boot to Windows, it doesn't recognise the FAT32 partition as a disk at all.  Checking in Disk Management in Windows it recognises that there is a healthy partition formatted to FAT32, but the only option it will let me do on the partition is delete it!

I read somewhere else that FAT32 partitions can only handle up to 32Gb, so I used gparted again to resize the partition to 30Gb, but it's still not recognised in Windows!

Sorry for the long post, hope this is enough information for someone to help :)

---

### Post by Herman on 2005-12-16
Hi, 117, 
 Windows normally creates itself as a 'primary' partition. We are allowed either four of those on a disk, or three 'primaries' and one 'extended.' The extended one can house several 'logical' partitions, it is like a box that can be divided up into smaller boxes inside it. Linux doesn't care if it goes on logical or primary partitions, as long as you keep the logical partitions in one 'contiguous' space on your hard-disk, so they can be included in the 'extended' partition. (Box they go in).
  > Partition 1 - NTFS - 75Gb (my XP Pro install)
Partition 2 - FAT32 - 60Gb (for sharing media between Windows/Linux)
Partition 3 - ext3 - 65Gb (my Ubuntu / install)
Partition 5 - ext3 - 60Gb (my Ubuntu /home install)
Partition 6 - swap - 2Gb (my swap partition)
there's no Partition 4 for some reason? Okay now, another thing is; partition numbering. The four primary partitions have the numbers 1,2,3,4 reserved for them. If you have three primaries and then make a 'logical', it will 'skip' the number 4, as that is reserved, and start counting again from number 5.
Therefore, by the looks of it, your FAT32 partition is a 'primary', because it has the number 2. Now, I'm not sure whether that it's wrong, but everyone always talks about a 'FAT32 logical' partition for sharing data. I don't know why, but that's what I do too and it works okay for me.
Third thing: when I was trying to learn how to do it with my test computer to make the instructions for my 'sig link' install website, I found out by trial and error the way that works is to write the changes to disk for that FAT32 logical first, then create the other partitions. I don't know why that mattered, but it did for some reason. Otherwise, I think your method of getting Windows to recognise it through formatting it again from Windows side in disk management should work. I can remember doing that when I was experimenting and it fixed it fine.
Finally, I must add that I have had no formal training in these matters, all I know is what has worked for me by trial and error. I am still discovering new information about disk partitioning every day. I have done my best to give you the best advice I can, but some it might need correcting by someone who knows more.
So to sum up, the main point is: try making your FAT32 into a logical partition and see if that helps. And oh, yeah, by the way, it doesn't matter where on the disk it is located, Windows and Ubuntu will still 'see' it even if there are other partitions in between. As long as you keep your logical partitions all together in one 'box'.
I think this is all correct. Good luck with it :D (Herman)

---

