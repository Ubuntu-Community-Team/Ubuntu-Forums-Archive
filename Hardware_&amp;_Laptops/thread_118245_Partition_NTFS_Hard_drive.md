---
title: "Partition NTFS Hard drive"
date: 2006-01-16
forum: Hardware &amp; Laptops
---

### Post by Kieffer87 on 2006-01-16
Ok I have a drive that is half full, only used for storing my music etc. I want to partition the unused space on the drive to ext3 or 2 whichever will work best. Then I will copy the files to the new partition and repartition the old NTFS to ext 3 or 2.  Will this work? And then possibly merge them together?

---

### Post by aysiu on 2006-01-16
I think so, but honestly I don't really have a handle on what you're describing. Can you give some letters maybe? /dev/hda1 /dev/hdb1 /dev/hdb2? Or maybe some examples of which files would be copied where?

---

### Post by Kieffer87 on 2006-01-16
ok this is my second drive dev/sdb it is formated in NTFS, in which I have about 80GB of stuff such as .mp3s, movies etc. I can access it right now but I would like to beable to write as well. So I am trying to just "move the files around on the disk" rather than moving them to a complete different disk, as I do not have enough space on the other my dev/sda which has ubuntu installed. 
So basically
1. create ext3 partition using 99GB free on /dev/sdb
2. Copy files from NTFS partition to ext3 partition
3. Change NTFS partition to ext3.
4. Merge or combine both partitions into one or leave them be.

I hope that helps a bit.

---

### Post by Kieffer87 on 2006-01-16
I just decided to copy some files and ill have to get the other again later. but thanks for trying to understand my mess :)

---

### Post by morphodone on 2006-01-16
[QUOTE=Kieffer87]
1. create ext3 partition using 99GB free on /dev/sdb
2. Copy files from NTFS partition to ext3 partition
3. Change NTFS partition to ext3.
4. Merge or combine both partitions into one or leave them be.
[/QUOTE]

Yes you can do this...you may need a windows application to resize the ntfs partition.  Although, some linux applications may be able to do so as well.

Once resized, you can make a new partiton in ubuntu.

Copy over the files and delete the ntfs partition.

Extend the ext3 (or whatever) partition.

You might try a live cd to do accomplish this...SimplyMepis, knoppix, etc...

---

### Post by aysiu on 2006-01-16
It can be done if you have enough space (it sounds as if you may have already solved it?).

Knoppix would do it just fine, but I would recommend [DiskDrake](http://www.ubuntuforums.org/showthread.php?t=114142)

---

### Post by Kieffer87 on 2006-01-17
I just decided to say screw it and copy over the essentials and I can always get the rest later as far as music goes. However I cannot get it to format. I went into system, admin, disks. and selected my drive and did a format to ext2 but when I try and make it accessible it just blinks and does nothing. Then if I restart its right back to NTFS. I just want to reformat the whole drive for ext2.

---

### Post by morphodone on 2006-01-17
[QUOTE=Kieffer87]I just decided to say screw it... and did a format to ext2 but when I try and make it accessible it just blinks and does nothing. Then if I restart its right back to NTFS. I just want to reformat the whole drive for ext2.[/QUOTE]

Haha, I like your brazen attitude.

First off, I would at least format with ext3...or reiserfs. Probably doesn't matter anyhow.

Second, sounds like you need to update you /etc/fstab.  If there is an entry in there for the drive with ntfs as the filesystem then it's not going to mount properly.  

So, 

sudo cp /etc/fstab /etc/fstab_backup
sudo nano /etc/fstab

change whatever filesystem is ntfs to ext2

sudo mount -a

---

### Post by Kieffer87 on 2006-01-17
Your my new hero :) I kept having trouble because I forgot that I added the info in the fstab to mount it as NTFS. finally got her up and running. Thanks again!

---

### Post by morphodone on 2006-01-17
[QUOTE=Kieffer87]Your my new hero :) I kept having trouble because I forgot that I added the info in the fstab to mount it as NTFS. finally got her up and running. Thanks again![/QUOTE]


awesome, glad to hear you got it running ;)

---

