---
title: "Dual Boot With Shared Partition"
date: 2009-10-19
forum: Installation &amp; Upgrades
---

### Post by NTHQ on 2009-10-19
I currently have Windows Vista and Ubuntu 9.04 in dual boot with each having it's own partition on my hard drive. I want to do a clean install of Windows 7 and Ubuntu 9.10 when it comes out but I also want to have a third partition that can be accessed by both OS's so that I can share files between them. This partition would contain all my music, videos, documents, and also my /home directory so that I can keep all my settings whenever I reinstall Ubuntu.
How would I go about this? Which OS should I install first to make the job most simple? Which file system should I use for the shared partition? I know that Ubuntu is capable of working with NTFS and that with a little extra, Windows can use ext3 so what advantage does one have over the other?
Also how big should the partitions containing the actual OS's be?

---

### Post by bulldog on 2009-10-19
Hi NTHQ,

Well to begin.how big is your hdd?

You should first install windows7 on a primary partition,the size is entirely your choice and you should use NTFS of course.

Ubuntu is another story,but basically you need two partitions,it doesn't matter if they are logical or primary,one is for the system and one is for swap,what is basically the same as the page file in windows,only it is on his own partition.

How would I do it.
Create a primary for windows 100GB
Create a primary for data 100GB
Create a primary for /home 100GB
Create an extended partition as big as the rest of the hdd
Create in the extended a logical 10GB
Create in the extended a logical 10GB
Create in the extended a logical for swap 2GB

Some explanation ,you can do it with other size partitions of course,but it's the idea what counts.
Windows is clear I presume.
The reason I made several primary is that if your windows is running out of space,you can easily give space from the data partition to your windows [max 100GB extra]
Then I go to the logical partitions.
I create two 10GB partitions,one you will use for your current ubuntu install,which only will have your /  [system files] which would be more than sufficient and your personal data will be located on the primary which I created as /home.
If in the near future you want to install a newer version of ubuntu,but you don't want the risk of loosing your current install,you just use the second 10GB partition,the same swap and the same /home folder.
Only use for the new install another login and password,it will create his own folder on your /home,and you can copy/paste all your data between the two ubuntu's.
If the second ubuntu is up and running well,you will use in most cases this one,and no more the 'old' one.
So when the next version comes out,you can install it on the 'old' 10GB partition.using the same swap and /home.

Filesystem.
Windows NTFS
Ubuntu system / ext3
/home ext3
Data NTFS
swap swap

---

### Post by Niko Johnson on 2009-10-19
Bull dog has a good point. i think that would be best. you can always check out your basic files like documents,music,pictures,etc... in ubuntu no problem just go to places > OS. then type in your password and you can retrive all your files from the other windows partition even if you didnt import them during the install

---

### Post by Mark Phelps on 2009-10-19
> **NTHQ said:**
> ... This partition would contain all my music, videos, documents, and also my /home directory so that I can keep all my settings whenever I reinstall Ubuntu...

AFAIK, the /home partition for Ubuntu must be a Linux filetype (typically Ext3 or Ext4 although others are permitted) and shared partitions between MS Windows and Linux need to be FAT32 or NTFS.

Also, entries in your /home partition will have absolutely NOTHING to do with MS Windows, as would entries in MS Windows <user> folder have absolutely NOTHING to do with Ubuntu.

You're better off NOT trying to share the stuff in /home.

As to data files, my experiences is that NTFS-formatted partitions work quite well for sharing data files.

---

### Post by NTHQ on 2009-10-20
Hi all and thank you for the responses.

Do I really need to create the swap partition myself? I thought it would do that on it's own.

And my hard drive is 320GB by the way.

---

