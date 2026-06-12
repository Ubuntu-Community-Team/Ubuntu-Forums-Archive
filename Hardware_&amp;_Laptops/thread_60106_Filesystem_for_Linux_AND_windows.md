---
title: "Filesystem for Linux AND windows"
date: 2005-08-26
forum: Hardware &amp; Laptops
---

### Post by otey on 2005-08-26
Hi

I have a question conserning one of my harddisks. On one of my harddisks (linux) i have a reisersfs partition and a swap. On the other harddisk i have 40G ntfs (windows) and 120GB ntfs (Music n stuff). But in linux i can't mount ntfs for read/write  so i want to format using a new system on the harddisk partition. 

But what should i use. It has to work for both Linux and Windows xp.

And how do i do it? how do i format the harddisk partition to the new system?

---

### Post by Pekkalainen on 2005-08-26
I've heard FAT32 works for both Linux and Windows, dont know how to mount that type though  :---)

---

### Post by Scrambler on 2005-08-26
[QUOTE=Pekkalainen]I've heard FAT32 works for both Linux and Windows, dont know how to mount that type though  :---)[/QUOTE]
 The only file system which currently safe to use for both systems is FAT32, unfortunately. Setting up NTFS R/W is possible but not recommended for inexperienced users.

Mounting an FAT32 partition:  mount -t vfat -o umask=000 /dev/hdb1 /media/windisk

Of course you would first have to create a FAT32 disk using fdisk. You will have to know which disk is the one that should hold the new file system, probably your slave disk as /dev/hdb?

fdisk /dev/hdb and create a new partition and change the type to C (FAT32 LBA) BUT BE CAREFUL you are using the correct disk. Also note that all data WILL BE LOST on that disk!

   Cheers, Uwe

---

### Post by th3p14gu3 on 2005-08-26
or u could use mkfs.msdos -F32 /dev/hdb[partition number] in linux
add 
/dev/hda2       /mnt/hdb[part number]       vfat    rw,umask=000    0       0
to your /etc/fstab to automount the partition at boot

if the partition you want is on your first harddisk (hda) replace hdb with hda in the above.

---

### Post by John Nilsson on 2005-08-26
You could use [ReiserFS](http://rfsd.sourceforge.net/)

---

### Post by s_p_a_r_k_y on 2005-08-26
i hear 
```
format c: 
```
works well when typed in dos

---

### Post by otey on 2005-08-27
Thank you all. I'll go try FAT32. I'll let you know how it goes.

---

### Post by otey on 2005-08-27
I think i will go for the "mkfs.msdos -F32 /dev/hdb[partition number]"
But just to be sure. The ntfs partition (as it is right now) is mounted as hdd5...

so what i need to write (in the gnome terminal) is 

sudo mkfs.msdos -F32 /dev/hdd5

Right?

---

### Post by John Nilsson on 2005-08-27
[QUOTE=otey]I think i will go for the "mkfs.msdos -F32 /dev/hdb[partition number]"
But just to be sure. The ntfs partition (as it is right now) is mounted as hdd5...

so what i need to write (in the gnome terminal) is 

sudo mkfs.msdos -F32 /dev/hdd5

Right?[/QUOTE]

 Just to be sure. You do realize that you'll destroy all data on that partition?

---

### Post by otey on 2005-08-27
[QUOTE=John Nilsson]Just to be sure. You do realize that you'll destroy all data on that partition?[/QUOTE]

Yes i know. The partition is now empty. the only thing left is a folder with some volume data for windows xp. The data is now on my brothers computer.

---

