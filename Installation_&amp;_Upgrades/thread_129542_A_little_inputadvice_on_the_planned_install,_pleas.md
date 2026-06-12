---
title: "A little input/advice on the planned install, please."
date: 2006-02-14
forum: Installation &amp; Upgrades
---

### Post by Coelocanth on 2006-02-14
Greetings!

After much research I think I've decided what I want to do with my dual-boot. Here are the specs:

250 GB SATA hdd with Windows XP installed (NTFS) on a single 250 GB partition (actually it works out to 233 GB of actual hard drive space, but anyway...). I'll repartition, leaving 43 GB for Ubuntu. 

This 43 GB I think I'll divide as follows:

20 GB FAT32 logical partition
2 GB swap file (is this too much? Just right? Not enough? I have 1 gig of RAM)
19 GB for the linux partition.

The questions I'm wondering about are;

1)  should I forget the swap file and let the install automatically partition the free space (which would be 21 GB), creating its own swap file and primary or should I allocate the swap file myself?

2) should I allocate another partition to use as /home and have the OS on its own primary partition - I read in one of my numerous browsings that this may be a good idea  (forgive me if my terminology is off or if this is a ridiculous question - I'm still learning) or just let the install decide what's best?

Many thanks for any advice.

---

### Post by Herman on 2006-02-14
> 1) should I forget the swap file and let the install automatically partition the free space (which would be 21 GB), creating its own swap file and primary or should I allocate the swap file myself?Yes. I would not worry too much. Just take it easy and let the partitioning software handle it. Believe it or not, the installer and partitioning software for Ubuntu really will get it right. That's my opinion anyway. You have plenty of RAM and plenty of HD space anyway, swap size won't be a big issue for you. Just pick 'automatically partition the free space'.

> 2) should I allocate another partition to use as /home and have the OS on its own primary partition - I read in one of my numerous browsings that this may be a good idea (forgive me if my terminology is off or if this is a ridiculous question - I'm still learning) or just let the install decide what's best? This is a matter for personal opinion and much debate. Here's my opinion on the subject. Others will disagree.
This is a good idea if you are planning on trying Ubuntu for a short time and then maybe you'll want to try out some other Linux distro and you don't want to have to re-install everything from scratch all over again. Lots of people like doing things this way. Some say it will make it easier to upgrade to Dapper when it comes out. (Dapper is not recommended for general use yet). You will waste a little disk space, because you will be fixing the size of your / partition so you will maybe want to allow a little extra there that you will never use to allow room for software you may or may not add. 

The advantage of not having the two partitions seperate is that directories (folders) can expand and contract as needed (flexibility), whereas a partition is fixed in size and rigid.

Actually, You won't really need a seperate /home partition to upgrade to Dapper when the time comes, because you can just do [something like this.]("http://www.ubuntuforums.org/showthread.php?t=126906&highlight=dist-upgrade")
Personally, when I decided to try out other Linux flavors, I found it much more convenient, and tidier, to just multi-boot. Having a lot of seperate partitions for more than one operating system just makes a big confusing mess of your hard disk when you multi-boot. (I think there is a way to get more than one operating system to share the one /home though, that's an interesting thought).

I prefer to keep to single partition installs myself. I like to keep things simple, neat and tidy.
I think choose 'manually edit the partition table' until you have your fat32 partition made, then just choose 'automatically partition the free space' after that. This is just my personal opinion, you are free to experiment and try anything you like. Maybe try installing two or three times and see which arrangement you prefer before you get too many files. It only takes half an hour or so each time, and you can always just delete the partitions again and re-install a different way.  :-D (Herman).

---

### Post by Coelocanth on 2006-02-14
Herman, thanks very much for the reply. I think your advice is sound and will let the installation take care of the details (easier for me anyway!) and I'll be using your excellent guide for the installation, so I'm confident I'll be up and running on Ubuntu in no time!

Thanks again. :D

---

