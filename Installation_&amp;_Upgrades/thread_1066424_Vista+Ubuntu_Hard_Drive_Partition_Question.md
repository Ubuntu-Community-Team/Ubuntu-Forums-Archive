---
title: "Vista+Ubuntu Hard Drive Partition Question"
date: 2009-02-10
forum: Installation &amp; Upgrades
---

### Post by huruixd on 2009-02-10
Hi friends, 

I have problem on the vista partition. My laptop has a 160GB hard drive. I installed vista business and ubuntu8.10 on it. Here is a snapshot of the disk management.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=102914&stc=1&d=1234318724[/IMG]

As you can see, there is an unallocated space of 53.98GB is still available. I would like to format it as D: drive and E: drive under Vista. I clicked the mouse right button, select "new simple volume", but it says: You can not create a new volume in this unallocated space because the disk already contains the maximum number of partitions. 

Does anyone know how to deal with this? A step by step guide is appreciated.

---

### Post by bicyclebarron on 2009-02-10
In Microsoft world you only get 4 partitions. These can all be basic or if you want more than 4 you can have one extended partition with logical drives assigned to that partition. Although most desktops now multiple partitions on one OS aren't as necessary as they where a few years ago.

---

### Post by huruixd on 2009-02-11
I was wondering how I could create a extended partition based on my current hard drive settings. I just want to add two new partitions without hurt any of the existing ones.

---

### Post by caljohnsmith on 2009-02-11
How about booting into your Ubuntu install, open a terminal (Applications > Accessories > Terminal) and post the output of:
```
sudo fdisk -lu
sudo sfdisk -d
```
And please identify all the partitions listed. And just to clarify, are you trying to make two partitions from the unallocated space on your drive? Do you want those partitions to be NTFS? Will they be for file storage or do you plan on installing another OS to either partition?

---

### Post by DarkfireSG on 2009-02-13
How do you edit and create new partitions with terminal? The Ubuntu partition editor cant find how large my primary partition is and it wont let me edit it without formating

---

