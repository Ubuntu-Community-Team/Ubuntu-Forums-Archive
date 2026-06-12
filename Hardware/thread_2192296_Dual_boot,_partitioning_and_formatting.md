---
title: "Dual boot, partitioning and formatting"
date: 2013-12-07
forum: Hardware
---

### Post by seanadd7 on 2013-12-07
[CENTER]I have a dual booting partitioned hard drive in my acer laptop, which was given to me from an IT guy friend set up with windows 7, and i guess i ****ed up windows dicking around and deleted something i couldnt fix. So i started to learn a lil bout linux and now i have ubuntu lxde 12.04 and the damaged windows 7 on the ntfs boot partition. Now according to the Disk utility program the memory of the drive is divided in order of 1st partition is flagged as bootable and is in the format of HPFS/NTFS (0x7), the second partition being 40 GB and same format, the next two partitions are for ubuntu 12.04, the first being a 120 Gb extended format partition, and the other being the 119 Gb ext4 version1.0, and a 1.1Gb minix linux swap type partition. 

How do i format the drive without ****ing it up mbr? I dont use windows anymore but i heard that if the windows mbr is copied, it will **** it up. I have a Tb external ntfs hardrive and another smaller dual format ntfs and FAT partition with a backup of the ****ed up windows 7 VHD file, and a backup .img of the OS and a .zip. I just dont want to delete those files so i need step by step instructions. Making my laptop hard drive  all Linux ubuntu extended format and ext4 and i guess the swap too.









help, i can be more specific, thats why i came here cause linux users are smart : )
[/CENTER]

---

### Post by mörgæs on 2013-12-07
Please watch your language.

---

### Post by seanadd7 on 2013-12-07
sorry about the language, i wont fail it again.

---

### Post by seanadd7 on 2013-12-07
i like the lightweight desktop enviroment gnome shell for 12.04. Unity is more like windows and thats  why people should forget about windows, cause with these people helping with their vast assortment of technical detail and knowledge.

---

### Post by oldfred on 2013-12-07
The MBR boot loader is generic and generic boot loaders will boot Windows just as well. There may be a serial number hidden in the MBR between boot loader and partition table, and DRM Windows software may have serial numbers hidden in the sectors after the MBR but before first partition.
Generally Windows based backup software backups up Windows correctly. Or full hard drive image works.

       How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

Do you want to keep Windows or a NTFS partiiton for Windows. That must be primary and is better if first, but only real requirement is a primary boot partition.

There is no one right way to partition. It depends on what you want and plan to do in the near future. I find my own optimal partition plan is not so good a couple of years later, but then it may be time for a new hard drive. Or excuse for one to my wife. :)


 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:

  MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

---

