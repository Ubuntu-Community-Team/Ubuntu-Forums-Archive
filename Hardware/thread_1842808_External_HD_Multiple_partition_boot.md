---
title: "External HD Multiple partition boot?"
date: 2011-09-12
forum: Hardware
---

### Post by Ikthel on 2011-09-12
The title might be a tad bit misleading I think, sorry its 4:36am were I am and I'm a tad bit out of it, but basically I was wondering if it was possible to partition part of my 500gb Segate external HD and use one partition as a bootable USB stick and the 2nd partition for normal storage? Any help would be much appreciated ;)

---

### Post by Basher101 on 2011-09-12
This is very possible. I got myself a bootable partition on my external WD 320GB HD with a fresh install of Ubuntu for recovery purpose. Just make sure that you install the ***_[SIZE="3"]Bootloader[/SIZE]_*** on your external hard disk. If you dont know how i will upload a screenshot

---

### Post by Ikthel on 2011-09-12
Please do so :) and thank you for the help. :smile:

---

### Post by Basher101 on 2011-09-12
Before i upload it i need more specifications. Do you already have a partition where you can install ubuntu on? or do you have to create it? i can also guide you with the creating. There are 2 ways of doing this tho, 
1. You can choose use all space so it will format the WHOLE drive to ext4 filesystem. The whole installation from then on is all automatic. After the install you can shrink the one and only partition to use the space as storage.

2. You create the partitions before the install and specify your partitions for Ubuntu and storage beforehand.

---

### Post by Ikthel on 2011-09-12
I currently have 3 partitions and know how to do that, I currently have around 100+Gbs free in my 3rd partition which I can cut into yet another smaller partition, what size do you recommend?

---

### Post by Basher101 on 2011-09-12
For ubuntu you need 2 partitions. 1 for the ext4 filesystem where the OS itself will be installed, and a second partition _**as big as your RAM**_ for SWAP. SWAP is a partition where un-needed processes are temporarily written to in order to free up RAM. As for size, a minimum should be 20GB. You can also store files on a NTFS partition and share it as storage for ubuntu and Windows. I do the same, i got on my 640 GB Internal HDD 10 GB for Ubuntu (Just OS), 30 GB for windows 7 (also OS+all the annoying updates..) and all the other space as shared storage  (NTFS-partition).

edit: forgot the screen..
ps. i just heard a nuclear power plant somewhere in france exploded...i will go watch some news and brb with the screenshots

---

### Post by Basher101 on 2011-09-12
Okay if you set your free partitions you gotta first set the _**[SIZE="2"][COLOR="Red"]Mount points[/COLOR][/SIZE]**_ as seen on the first screen. Then at the bottom is your bootloader device. Select your [COLOR="red"]**_EXTERNAL HDD_**[/COLOR], /dev/sd_**[COLOR="red"]b[/COLOR]**_ not a partition like /deb/sdb**_[COLOR="red"]1[/COLOR]_**. The letter could be another, just make sure no number is behind it. After you got that all hit install and your done^^

---

### Post by Basher101 on 2011-09-12
Okay now step by step explanation:
Step 1: Choose on the install window Something else
Step 2: Specify your Partitions for use. Click on the partition you want to install Ubuntu on and then click on the button "Change" then a window will pop up and make it look like on Step 3
Step 3: Make it ext4 filesystem, check the reformat box and choose "**_[COLOR="Red"][SIZE="3"]/[/SIZE][/COLOR]_**" as the mount point.
Step 4: Specify your smaller Swap partition as swap. Do the same as for the ext4 filesystem, but choose Linux Swap instead. No reformat needed
Step 5:Look at the bottom and choose your bootloader device. Make sure its your entire External HDD, otherwise you WILL get boot problems.

---

### Post by Basher101 on 2011-09-12
if you still have questions feel free to ask

---

