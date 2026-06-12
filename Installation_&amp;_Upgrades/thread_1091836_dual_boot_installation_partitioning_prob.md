---
title: "dual boot installation partitioning prob"
date: 2009-03-09
forum: Installation &amp; Upgrades
---

### Post by petemga on 2009-03-09
This is my first time trying to install ubuntu and/or Linux for that matter and I am a complete noob at it. I began the  installation and once I get to the partitioning part where it says "Prepare Partitions" and shows my HD's. I pick the first of my 3 drives, which is the one with Windows XP on it. It is an 80GB drive with 58gigs used and the rest free, so I select the drive (dev/sda1) and click on edit partition when another box pops up that says "Edit a Partition". The choices in this box are "new partition size in megabytes", "use as:" with a drop down box that has choices like NTFS and swap area, a check box that says format the partition and another drop down box that "says mount point" with /windows and /dos in the drop down box. So I enter a partition size of about 5GB or 5200MB and select NTFS from the first drop down box and select OK and then I get a box that pops up that says "Too small size". I have searched the forums and read a lot, but am still quite a nood at linux. All I want to do is create a partition in my C: drive so i can istall ubuntu which in all the guides I read seemed so easy. 

Thanks ahead for you time.

---

### Post by upchucky on 2009-03-09
xp needs about 25 gig, this is because some brainless developers are still writing programs that will only install on the c drive. the only thing that should be on a windows c drive is the operating system period, that way when windows self destructs as it is designed to do, it is a simple matter to just restore it from your back up image that you were clever enough to make using NTFSclone, and not have to reinstall any other programs and files. and the fact that windows by default dynamically changes its swap file size whether it needs to or not, in fact it uses the swap file even if there is excessive amounts of ram.

Ubuntu core needs at least 10 gigs, and a 1 gig swap file that it never uses, however since i have tons of room I also give linux 25gigs

I have an existing NTFS "D" drive of 250 gigs for all windows files.
I created a 250 gig EXT3 partition for the ubuntu home directory, this ensures that in the unlikely event that I have to re-install ubuntu any files and programs in ubuntu stay intact.

not sure why you want a fat 32 partition.

If you are really interested in understanding the partitions and how it all comes together, then get the knoppix cd, its free. it has two partition managers on it and safely works with the exotic ntfs windows partitons, it also lets you edit any files you need in windows and ubuntu to get both working as a dual boot, this includes setting up the menu.lst file in grub to tell it the drive info and how to set up the chainloader for windows.

you may also need advanced supergrub disk, it will repair the master bootloader in case either os will not boot.

---

### Post by petemga on 2009-03-09
I dont want a FAT32 partition. I was just trying to add the ubuntu install to my C: drive which has like 22GB of free space and that is my dilemma. I have enough free space to partition the drive to add the ubuntu installation. Are you saying that Windows wont let me add the install the the C: drive?

---

### Post by gloxer54 on 2009-03-09
First, the MOST important thing to do is defrag Windows.  Do it a couple of times and anything else that might clean up that partition. After that, one can use gparted(gparted-live-0.4.3-2.iso @ [http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)), to re-size that C: drive down to say, 60 or 62 GB or so. You have to leave that swap file(page file).  You have to burn that ISO and reboot to it.  I believe that after you look at that a few times, you will then understand how it works. Read a little here: [http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)  
  The very first time I installed Ubuntu I had little idea what I was doing.  I had Windows 2000 pro and it worked out to a duel install no problem.  Maybe I was lucky, maybe it was Linux automagic, I do not know.  Anyway, best of luck!

---

### Post by petemga on 2009-03-10
I have O&O defrag that runs regularly. The disk is already sized to 58GB leaving 22GB free on the 80GB total aize of the drive (give or take a little bit for overhead). I am booting from the ubuntu iso and go through all the steps to install ubuntu. Language, keyboard, etc. etc. When I get to the patitioning stage, it wont let me partition a 10GB size partion of ^^said disk^^. If I have an 80GB drive (C: ) with Window$ and some other various files on it that total in of about 58GB on the 80GB disk, that should leave me more than enough room to create a 10GB partition, no? Ununtu wont let me do it. Can someone point me in the right direction, please? :D 

Thanks in advance!!!!!!!!!!!!

---

### Post by vginov on 2009-03-10
Here is a step by step tutorial for Dual boot with windows and Linux 

[http://www.vginov.com/linux/fedora/Installing%20fedora%2010/index.php](http://www.vginov.com/linux/fedora/Installing%20fedora%2010/index.php)

You can watch the video or you can follow the screen 

IF you have problem in installing ubuntu then take a look at this page 

[http://www.vginov.com/linux/ubuntu/install/index.php](http://www.vginov.com/linux/ubuntu/install/index.php)

Hope you are able to fix the problem

---

### Post by vginov on 2009-03-10
If you want to install ubuntu as dual booting then why do you delete the windows partition. 

Leave the windows partition and choose the disk (sda2 or sda2) which does not have any OS and create a new partition in that drive and first create a swap then create the root (/). swap is must. 
If you have any problem then follow the above link 

you can do it..

---

### Post by petemga on 2009-03-10
Thanks! I am going to look at the those links right now. I am not trying to delete widows, I want to keep it for gaming and for some programs I need for work. I will let you know how it goes. I think I will move some files around and use the 2nd disk for the ubuntu install even though I would like to use the 1st (C: ). ;)

---

### Post by petemga on 2009-03-11
in the 2nd video ^^above^^ posted by Vginov about ubuntu where he is creating his partitions is where I get stuck. He makes his 1st partition (swap) 1000MB and it works fine. I am doing exactly the same thing he is doing except I get a pop up box that says "Too small size". What is causing this? I do exactly what the guy in the video does and I keep getting this error, I am stumped. I have read and searched and cant solve the prob. I just built this computer---> Its got an E8400 wolfdale with a slight OC to 3.5 air cooled, 2 gigs of ram, over a TB of storage (4 HD's total) and Windows XP with recent updates. help

---

### Post by petemga on 2009-03-12
nobody?

---

