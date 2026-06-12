---
title: "Hosed my MBR while cloning dual-boot setup"
date: 2009-05-25
forum: Installation &amp; Upgrades
---

### Post by L14UX_1NS1D3 on 2009-05-25
Hello everyone. 
I'm actually writing this from a ubuntu livecd due to the fact that while attempting to clone my laptops partitions onto a new, larger 160GB sata laptop HD I screwed with the grub setup and now when ever I boot into either drives I always get "grub: error 15", meaning that grub was not able to find the kernal/files needed to boot. 

I started this thing a few days since I got a usb to hard drive adapter cable to hookup a 160gb 3.5 sata and copy files over from the sata hd sitting my laptop. 

I considered two ways I could go about this.

1. do a byte for byte copy of the entire 80gb hd onto the larger drive
2. use clonezilla to copy the drive.

I went with the latter. I first popped in a older version of clonezilla but it didn't play nice with the ext4 partitions on the drive so I went and downloaded latest version then I was able to copy the partition over.

I have a really strange partition setup on my drive. My machine came preinstalled with vista and a recovery partition for the vista install. I moved over the recover dir and installed ubuntu a swap space and a fat partition to share files for either OS I'm booted into.

I didn't have much of a hitch with coping the partitions over until clonezilla tried to install grub.

Here's where my nightmare started. I did this a few times, I copied over the ext4 partition with ubuntu a few time. Everytime clonezilla finished copying the partition over it would attempt to install grub and fail.

I read tutorial about installing a grub to the MBR here:[URL="http://ubuntuforums.org/showthread.php?t=224351"]
http://ubuntuforums.org/showthread.php?t=224351[/URL] 

after executing all the commands I booted back into the with with the copied partitions and it would say "grub 1.5" and then just hang at "error 15".

I'm going to use "super grub recovery disk" and see what happens.

I feel pretty stupid after this escapade. And I still don't have any clear answers. Your help is greatly needed/appreciated. ](*,)

---

### Post by charliko on 2009-05-27
I was getting an error about the partition not being labeled correctly and needed to leave the Windows install disk in the tray to get Windows going.  Unlike myself  you have probably already been inside the setup of the cmos/bios and determined what hard disk is **first** and perhaps what hard drive is master.  After I had downloaded SGD I discovered that the first hard drive listed under Hard Drives was not the correct one.  After I changed that setting, Voila!!  It booted without the install disc in the cd/dvd tray.  At that point I could at least use WUBI.  

I hope it could be that simple for you too.

-Charlie

---

### Post by L14UX_1NS1D3 on 2009-05-27
Thanks for the tip but I know what partitions I have windows and ubuntu on. I was also able to find them by getting to the grub menu on SGD and hitting tab to list the possible options. For some reason I am not able to get the kernel to be seen even after I type the complete name. This is really confusing because I typed "/" and it listed the possible directories but when I entered the /boot directory tab would not complete the file name for the kernel or list any other files in that dir for that matter. I think that maybe the partition is not mounted but if it would not be mounted how can is see the folders in the root directory of ext formatted partition with ubuntu on it.

---

