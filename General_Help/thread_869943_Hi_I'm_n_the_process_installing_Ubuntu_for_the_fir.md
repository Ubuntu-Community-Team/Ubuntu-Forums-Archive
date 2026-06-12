---
title: "Hi I'm n the process installing Ubuntu for the first time!"
date: 2008-07-25
forum: General Help
---

### Post by mcnr on 2008-07-25
I'm adding a bigger hard drive and I'm going to have a partition/partitions for Ubuntu.  From what I've read I should have 3 partitions for Ubuntu /home /ext3 and a swap.  From what I read previously I needed to have the Ubuntu drives format in FAT32 but I also read that there is a driver(NTFS-3G)that will allow me to use NTFS.  So do I really need the /ext3 partition? Can't I use the NTFS driver and read off the existing partition that are NTFS? I know - I think :)- that the swap also needs to be FAT32. I know I'll have more questions.

Thanks 

Marc

---

### Post by gimlithedwarf on 2008-07-25
Hi Marc, is ubuntu going on its own drive?

---

### Post by Elfy on 2008-07-25
I don't know quite what you've read but you need linux compatible parttitions to run the os - you can access ntfs and fat partitions for data. You will need at the least a / and swap partition - it can help to have /home when you come to reinstall or upgrade.

Swap will need to be linux swap, / and /home are default ext3 but there are other formats you could use - just not windows ones.

Yopu could though install ubuntu with wubi - which is a type of virtual installation.

---

### Post by mcnr on 2008-07-25
Yes there will be a drive for Ubuntu and for the swap.  I forgot to add this before. In Partiton Magic for Dos I have drives that don't show up and I get and error message about the partition tables being bad. I've run chkdsk to fix the problems - supposed problems. I have no problems access the drives in XP, Partiton Magic for Windows sees them and when I use it to check for errors there aren't any and Windows "Computer Management/Disk Management" sees then also. I had read that Ntfs-3g was finicky about problems like this. That's one of my concerns.

Thanks

Marc

---

### Post by gimlithedwarf on 2008-07-25
ok mark, here's what you do, boot your ubuntu install cd and open the installer, tell it that you want to use ~50% of the drive for the system install and when you finish installing you should have your ext3 and swap partitions as well as some free space on your drive. Then in the free space you should be able to create another ext3 partition. Open the /etc/fstab as root with gedit (be careful with this one, make sure you know what your doing before you do it) and add a line for the new partition and set it to automount (there is plenty of help for this in google) finally use ln -s to create a symlink between the new partition and any folder in your main one (be sure that you aren't going to murder an essential folder when doing this, again be careful with any root commands you use)

---

### Post by mcnr on 2008-07-25
I'm in the process of setting up the partitions in Windows. Can't I just do that. I guess I'm being overly concerned with Ubuntu seeings these funky drives. The drive that I'm going o install Ubuntu on is OK and the partition for the swap is already FAT32 it's just the otehr drives. I think part of my confusion was over the ext3. The way it read it was a partition not a file system! So Ubuntu will convert the /home and /swap partition to ext3?

I like your name! Have you ever noticed how many reference there are to Tolkiens stuff in Led Zeppelin songs?

Marc

---

### Post by steveneddy on 2008-07-25
It's OK to set up the partitions in Windows, but the installer will format them in a non NTFS format that is compatable to Linux.

The Linux Live CD should be able to read the partition tables set up by Windows.

---

### Post by mcnr on 2008-07-25
I understand now. I thought that Ubuntu used FAT32 it can only see it and than it has to convert it to ext3.

Thanks!!!!

Marc

---

