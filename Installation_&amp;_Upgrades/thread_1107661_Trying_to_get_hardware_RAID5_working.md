---
title: "Trying to get hardware RAID5 working"
date: 2009-03-27
forum: Installation &amp; Upgrades
---

### Post by Droidling on 2009-03-27
About a year ago I tried out ubuntu for the first time. I was trying to put together a file server, with a RAID based on a Highpoint Rocketraid 2220 controller. I didn't have much luck. Finally, I gave up and went back to MS products. 

I'm ready to give this another try. I got further this time than I ever have before but now I'm stuck again. Here is the background:

I replaced the Highpoint RAID card with a 3Ware 9500S-12. The 9500 series was listed as fully supported. It currently has 2 x 400G and 6 x 750G drives connected. I installed Ubuntu 8.10 onto a 150G PATA drive connected to the mother board controller. I installed all the updates and added a copy of Gnome Partition Manager (GParted). After the install I used the 9500's bios utility to create a mirrored drive out of the two 320G drives, and a RAID5 array out of the six 750G drives. I was able to create a partition on the mirrored drive. GParted said it was successful, but I am unable to use it. Each time I try to write to it an error message say I don't have proper permissions? Is there an application that sets permissions?

I hit a second problem when I tried to partition the RAID5 array. The unallocated size was 3.41 TB I believe. I recieved an error when I tried to apply changes to make the new partition. After reducing the RAID size by removing some disks to get it down to 2TB I tried to create the partition again. I got the same error. Here are the details from GParted:

GParted 0.3.8

Libparted 1.8.9

Create Primary Partition #1 (ext3, 2.05 TiB) on /dev/sdb  00:00:00    ( ERROR )
     	
create empty partition  00:00:00    ( SUCCESS )
     	
path: /dev/sdb1
start: 63
end: 4394452229
size: 4394452167 (2.05 TiB)
set partitiontype on /dev/sdb1  00:00:00    ( ERROR )
libparted messages    ( INFO )
     	
Assertion (ped_partition_is_active (part)) at ../../libparted/disk.c:1224 in function ped_partition_set_system() failed.
 

Any ideas why GParted would be giving me these errors?

Terry

---

### Post by dean123 on 2009-03-28
Why don't you use "parted" instead? 

Open a terminal, run

# parted /dev/sdb (sdb is the raid5 array)

then use fdisk to partition the raid1 array

# fdisk /dev/sda (assuming sda is the raid1 array)

I have never used Gparted but I try to avoid using GUI 
apps whenever possible.

---

### Post by Droidling on 2009-03-28
I'm really inexperienced with any Unix derived operating system. I was hoping the GUI would give me enough hints so I wouldn't be constantly bothering people with questions. That and using GParted was described in the online help for adding a drive. I don't know how to use parted or fdisk. I'll have to look and see what they do.

If anyone thinks that GParted should work for this, I'm starting to think I'm running into a large disk limit of some kind. I can partition and format a 1TB partition on the array. I then resized it to about 1.5TB. When I tried to increase the size to the full 2.05TB of the array Gparted produced a 47Gb drive instead.

Terry

---

### Post by Droidling on 2009-04-03
I have been trying to get to know Parted. With my lack of experience it took me awhile to find the documentation. I still can't figure out how to close a MAN page. I seem to remember there was a hot/escape key for this?

Currently I have a hardware RAID 5 configuration of 6 x 750Gb SATA disks. I was able to get GParted to create a 1.41Tb FAT31 file system on it. Parted gave me this information about it.

(parted) print                                                            
Model: 3ware Logical Disk 01 (scsi)
Disk /dev/sdb: 3750GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  1551GB  1551GB  primary  fat32  

I have some questions:
1. Is FAT32 a good choice if I need to share this with computers runing other operating systems, like W2000, XP and VISTA?

2. Can I just resize the partition up to the full size of the device? What would be the command parameters to do this?

3. Is anyone familiar with the 3WARE Management software for the 9500 series? I have been using the BIOS Setup so far, and it has only limited options. Will the 3WARE software allow me more options, like email alerts, adding disks to an existing array, setting up an auto-rebuild with a standby disk in case of a disk failure?  

4. The MAN page for Parted says,"The  parted  program  is  fully  documented  in  the info(1)  format  GNU  partitioning software manual which is distributed with the parted-doc Debian package." How do I get to this documentation? If there is a newcomers FAQ that would tell me how to find and use all the documentation that might be the best thing for me to read.

Please help

Terry

---

### Post by Droidling on 2009-04-05
Why can't I partition my RAID array as 1 large filesystem? I deleted the existing partition and used fdisk to get up to 2.2TB. fdisk gave me a range of 1-455904 for the first cylinder but only 1 to 267349 for the last cylinder.

[INDENT]Command (m for help): n
Command action
   e   extended
   p   primary partition (1-4)
p
Partition number (1-4): 1
First cylinder (1-455904, default 1): 1
Last cylinder, +cylinders or +size{K,M,G} (1-267349, default 267349): 
Using default value 267349
[/INDENT]

I formated it using mkfs -t msdos /dev/sdb1, then opened parted to try to resize it to to the full drive size. At least I think that is what using 1 for START and -1 for END should do. I still only get 2.2TB out of 3.75TB.

[INDENT](parted) resize 1 1 -1
(parted) print
Model: 3ware Logical Disk 01 (scsi)
Disk /dev/sdb: 3750GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  2199GB  2199GB  primary  fat32             

[/INDENT]

What's wrong here?

---

### Post by Droidling on 2009-04-06
I keep waiting, but no answer. If no one here has an idea could someone at least suggest another group where I can ask? Is there a central Linux group that might know the limitations of the file system and programs like parted and fdisk?

---

### Post by dean123 on 2009-04-07
Did you look at this KB article 3ware site? It shows how to use parted to create a partition > 2TB. 

[http://www.3ware.com/KB/article.aspx?id=11920](http://www.3ware.com/KB/article.aspx?id=11920)

---

### Post by ronparent on 2009-04-07
You may have to assemble your array with mdadm or load dmraid before gparted will recognizes it as a raid array permiting you to partition it with gparted as an array? I have only limited experience with a raid0 and had to use dmraid to accomplish this. Until then gparted would only recognize individual disks with unpartioned space. 

For your purpose, since it is a clean set of disks (?), you may want to use mdadm (I was too timid to since the command syntax didn't assure me that 'assembling' my existing array wouldn't destroy the contents). I would suggest addressing your questions to the Server Platforms section of this forum for more expert advise. bump

---

### Post by Droidling on 2009-04-07
> **dean123 said:**
> Did you look at this KB article 3ware site? It shows how to use parted to create a partition > 2TB. 

[http://www.3ware.com/KB/article.aspx?id=11920](http://www.3ware.com/KB/article.aspx?id=11920)

Thank you! This looks very promising. I'll have to wait till I get home to try it out.

Terry

---

### Post by Droidling on 2009-04-07
> **ronparent said:**
> You may have to assemble your array with mdadm or load dmraid before gparted will recognizes it as a raid array permiting you to partition it with gparted as an array? I have only limited experience with a raid0 and had to use dmraid to accomplish this. Until then gparted would only recognize individual disks with unpartioned space. 

I'm not familiar with mdadm or dmraid. It may take a day or two to digest the man pages. Currently gparted is seeing the array of 6 X 750 GB drives as one big disk (3.41TB) of unpartitioned space. I can partition it as 2 smaller file systems. It just won't let me make on big file system out of the entire disk. 

> For your purpose, since it is a clean set of disks (?), you may want to use mdadm (I was too timid to since the command syntax didn't assure me that 'assembling' my existing array wouldn't destroy the contents). 

There is nothing anywhere on this system that I'm worried about replacing. I can experiment with both. 

> I would suggest addressing your questions to the Server Platforms section of this forum for more expert advise. bump

Sorry if I posted in the wrong place. I thought 'Server Platforms' was for a different OS install package. If I can't get through this with the suggestions from you and Dean123 I'll try asking in the server forum. 

Thanks for answering. I was beginning to think I had committed some unforgivable breach of forum etiquette, and I was being shunned. 

Terry

---

### Post by ronparent on 2009-04-07
I don't think that one 6X750Gb Partition would be raid5. It lacks the redundancy that you would get from a combined striped and mirrored array. If that is what dmraid produced for you, then you need to either use differnt dmraid options or possibly mdadm.

By no means shunned. I for one saw your post a few days ago but thought someone more informed would be able to jump in with better guidance.

---

### Post by ronparent on 2009-04-07
You might have a glance at this site for information on mdadm: [http://linux-raid.osdl.org/](http://linux-raid.osdl.org/)

---

### Post by Droidling on 2009-04-07
> **ronparent said:**
> I don't think that one 6X750Gb Partition would be raid5. It lacks the redundancy that you would get from a combined striped and mirrored array. If that is what dmraid produced for you, then you need to either use differnt dmraid options or possibly mdadm.

I set up the RAID 5 array in the 3Ware BIOS setup  for the RAID controller. It has six 750GB physical drives in an array that theoretically would yield 3,750GB of storage space. Parted showed that it saw the Raid as /dev/sdb

(parted) print
Model: 3ware Logical Disk 01 (scsi)
Disk /dev/sdb: 3750GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number Start End Size Type File system Flags
1 32.3kB 2199GB 2199GB primary fat32

I just haven't been able to get it partitioned and formatted. The other oddity is that gparted listed the same device as 3.41 TB unpartioned space. It seems there is a bit missing. I can live with that I just mentioned it incase it was an important symptom of the main issue.

Terry

---

### Post by Droidling on 2009-04-07
> **ronparent said:**
> You might have a glance at this site for information on mdadm: [http://linux-raid.osdl.org/](http://linux-raid.osdl.org/)

Are both dmraid and mdadm raid management tools for the Linux software RAID facilities? If so I should ask about this in the server forum. I'm trying to do the RAID in hardware. I suppose I should ask if there is a reason to switch to a software RAID. 

Terry

---

### Post by ronparent on 2009-04-08
You could get more informed answers on configuring raid in the server forum. The only compelling reason to use a software raid solution is if you can't find your hardware drivers written for linux.

---

### Post by Droidling on 2009-04-08
> **ronparent said:**
> You could get more informed answers on configuring raid in the server forum. The only compelling reason to use a software raid solution is if you can't find your hardware drivers written for linux.

That's about what I thought. 

I should be able to set aside some time to try what Dean123 suggested soon if that doesn't work I'll be off to the server forum. 

Thank you for all your suggestions. 

Terry

---

### Post by ronparent on 2009-04-09
Have you looked at the following site? [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by Slim Odds on 2009-04-09
> **ronparent said:**
> I don't think that one 6X750Gb Partition would be raid5. It lacks the redundancy that you would get from a combined striped and mirrored array. If that is what dmraid produced for you, then you need to either use differnt dmraid options or possibly mdadm.

I think that you are confusing different types of RAID. The combined stripped/mirrored are RAID1+0 or RAID0+1 (sometimes called RAID10).

Also, dmraid requires hardware support. mdadm is a software solution.

I use RAID0 and mdadm. The fakeRaid stuff is pretty crappy (in my opinion).

---

### Post by ronparent on 2009-04-09
I defer. I'm definitely getting over my depth. Glad to see you arrive at the party.

---

### Post by Slim Odds on 2009-04-09
> **ronparent said:**
> I defer. I'm definitely getting over my depth. Glad to see you arrive at the party.

LOL :p

Not really an "expert", just a user who's tryin'

---

