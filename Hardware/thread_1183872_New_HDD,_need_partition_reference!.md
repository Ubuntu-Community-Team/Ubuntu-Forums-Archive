---
title: "New HDD, need partition reference!"
date: 2009-06-10
forum: Hardware
---

### Post by rbolio on 2009-06-10
So heres the deal: 

I've just bought a 500Gb Seagate internal HDD  ($119, for sale at Best buy! [do i get paid for saying that?]) 

Anyways, i've been using Ubuntu for a while but now with the expanded memory i've become ambitious....so heres my plan, i was wondering if anyone could help me achive it ...or atleast let me know if it is possible...


I want to partition the HDD into the following sizes:
1) 100 gigs for ubuntu
2) 50 gigs for windows XP
3) 350 gigs as a "common" partition between both partitions (aka. pictures, music,  movies etc.)


Is the third part possible? as in what format do i have to use? ext3?  
is it editable and accessible by both win/ubuntu??? 

I hope i expressed what i need help with properly...and i hope you can help me!

Thank you! :D

---

### Post by rbolio on 2009-06-10
Anyone?

---

### Post by rbolio on 2009-06-10
Ohhh come on guys!!! (and gals!)

---

### Post by jward3010 on 2009-06-10
Have patience my friend and you will receive a reply...

...in the morning, it's 1:38AM here in Dublin and my eyes are going red.

---

### Post by rbolio on 2009-06-10
So after a quick google search (shoulda done that first) 

Ive come to the conclusion that this can / will be done in the following way

1) 50g for windoze NTFS
2) 100g Ubuntu EXT3
3) 350g Shared data  FAT32


the given memory for each partition would most likely be for software .... 

does it sound reasonable? has anyone done this? should i lower the ubungu size?  any recomendations?


now, to learn about the ubuntu partition manaeger :D

---

### Post by mister_playboy on 2009-06-11
Use NTFS for the shared partition... FAT32 is acceptable on flash drives to extend their life, but is otherwise crap by modern standards.  Linux can make use of NTFS just fine.

I recommend the GParted Live CD as a good way to set everything up.  Always install Windows before Linux when dual booting.  Finally, if you ever need to resize the Windows partition (which is a huge PITA), use the free 30 day trial of Raxco DiskPerfect.  There is no free software tool that can do this job effectively... you need to move the pagefile and MBR to resize the partition.

---

### Post by jward3010 on 2009-06-11
I would make your OS partitions much smaller if you're creating a data drive for your personal files (music, pictures, downloads etc.). Ubuntu is surprisingly light for such a featured, complete OS and my installation never goes over 3GB's, but you need a little extra space for experimentation and temporary files especially if you burn DVD's and need a little space for ISO images. Windows XP is a little chunkier at around 6GB after a complete install and applications can be quite bulky. So here's my recommendation:

1st partition: 20GB NTFS: Windows XP (if Vista: 30GB)
2nd partition: 10GB ext3 / ext4: Ubuntu 9.04
3rd partition: 2GB swap: Linux swap
4th partition: 435GB NTFS approx. remaining: DATA partition

---

### Post by bol0 on 2009-06-11
I would come along with what jward3010 said above except leaving 4GB for swap as your RAM is 2GB size. These days NTFS should be fine for share partition on both systems. Install Win first and then Linux as Linux can see Win installed on the HDD but Win won't see Linux so you may get some issues trying to set up dual boot.

---

### Post by zgornel on 2009-06-11
The choice of the filesystem for the big data partition depends more on what OS you use more: if it is Linux, make it ext3 and use a windows driver for ext2/3 to read/write from it (you shouldn't play games installed on it as the performance is lower but for music/movies/documents it works perfectly). If the main OS is Windows, format it NTFS. Also, as for the order of installation of the OS's, it really does not matter: it is simpler to install windows first but you could also install linux then windows and later boot with a live cd and rewrite the mbr ;)

---

### Post by rbolio on 2009-06-12
oooo thanks for all the references :D 
But I have solved my problems... ( or so it seems :D)

I made a 50gig partition  for windows (NTFS)

and the rest is being used ATM for Ubuntu Studio 9.04 (ext3)


aparently theres a freeware that is for windows that allows you to access and modify files in ext3 partitions...so i guess that will do!

(hey , i only need to use windows for itunes and stuff like that)


thanks for all the help!

---

### Post by zgornel on 2009-06-12
> **rbolio said:**
> oooo thanks for all the references :D 
But I have solved my problems... ( or so it seems :D)

I made a 50gig partition  for windows (NTFS)

and the rest is being used ATM for Ubuntu Studio 9.04 (ext3)


aparently theres a freeware that is for windows that allows you to access and modify files in ext3 partitions...so i guess that will do!

(hey , i only need to use windows for itunes and stuff like that)


thanks for all the help!
Try here : [http://www.fs-driver.org/](http://www.fs-driver.org/) . I never had problems with it ;) .

---

### Post by rbolio on 2009-06-13
Funny you should mention fs-driver....

Heres the deal:


I've installed Fs-driver  (various times actually), how ever, each time I finish installing it, When I want to try it out by clicking in my "new" drive, windows wants to format it....

Did you have this problem? did I do something wrong in the installation?

---

### Post by zgornel on 2009-06-14
> **rbolio said:**
> Funny you should mention fs-driver....

Heres the deal:


I've installed Fs-driver  (various times actually), how ever, each time I finish installing it, When I want to try it out by clicking in my "new" drive, windows wants to format it....

Did you have this problem? did I do something wrong in the installation?
 Nope.

---

### Post by rbolio on 2009-06-15
Oh...damnit!

---

### Post by rbolio on 2009-06-16
OH GOD!...

So heres me bothering pros again.... heres the deal...

I deleted ubuntu Studio due to all the trouble it has given me.... 

So after deleting it, I have installed Jaunty (normal version) nad the following config has been done :

50 gig NTFS (windoze)
50 Gig EXT3 (ubuntu)
6  gig SWAP (it's recomended)
+350 gig  FAT32  (as a "common" library) 

However... ubuntu isn't detecting the FAT32 partition..... anything i have to DL or install?? what am I doing wrong???...

Thanks once more :D

---

### Post by zgornel on 2009-06-16
> **rbolio said:**
> OH GOD!...

So heres me bothering pros again.... heres the deal...

I deleted ubuntu Studio due to all the trouble it has given me.... 

So after deleting it, I have installed Jaunty (normal version) nad the following config has been done :

50 gig NTFS (windoze)
50 Gig EXT3 (ubuntu)
6  gig SWAP (it's recomended)
+350 gig  FAT32  (as a "common" library) 

However... ubuntu isn't detecting the FAT32 partition..... anything i have to DL or install?? what am I doing wrong???...

Thanks once more :D

If gparted or fdisk -l can see it as a fat32 partition, try mounting it manually in a folder of your choice ```
sudo mount -t fat32 /dev/sdaX /your/directory 
``` where sdaX is the associated device with the partition.

---

### Post by rbolio on 2009-06-16
FINALLY!!! thanks for your help!

THANK YOU!! :D

---

