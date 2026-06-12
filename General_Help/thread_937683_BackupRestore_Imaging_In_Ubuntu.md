---
title: "Backup/Restore Imaging In Ubuntu"
date: 2008-10-04
forum: General Help
---

### Post by klepto on 2008-10-04
I've been spoiled by apps in Windows such as Image For Windows and ShadowProtect. I am looking for an application where I can create a backup image and then later mount said image and extract files. I am looking into Image For Linux and TBIView as I own the whole set but never tried it. I'd prefer something I wouldn't have to get out of the OS to use. 

Any ideas? Thanks for the help as always.

---

### Post by azteech on 2008-10-05
> **klepto said:**
> I've been spoiled by apps in Windows such as Image For Windows and ShadowProtect. I am looking for an application where I can create a backup image and then later mount said image and extract files. I am looking into Image For Linux and TBIView as I own the whole set but never tried it. I'd prefer something I wouldn't have to get out of the OS to use. 

Any ideas? Thanks for the help as always.

Have you looked at trying to [SIZE=2]Back Up/Restore Hard Drives And Partitions With Ghost4Linux or Clonezilla?

There is a good tutorial for using Ghost4Linux here:

[http://www.howtoforge.com/back_up_restore_harddrives_partitions_with_ghost4linux](http://www.howtoforge.com/back_up_restore_harddrives_partitions_with_ghost4linux) 

and one for Clonezilla here: 

[http://packratstudios.com/index.php/2008/04/20/how-to-setup-clonezilla-on-linux-ubuntu-quick-start-guide/](http://packratstudios.com/index.php/2008/04/20/how-to-setup-clonezilla-on-linux-ubuntu-quick-start-guide/)


[/SIZE]

---

### Post by klepto on 2008-10-08
I went through this forum many times looking for reliable backup/restore software. I use two different software:

1.) Image For Linux, I bought the whole package BootIT, IFW, IFL, IFD, etc. It does byte for byte verification and the setup ran great on Ubuntu Hardy. Their free addon TBIView allows you to view/copy files in the image in either Linux or Windows(diff versions) and it is absolutely reliable. 

2.) Rdiff-backup, I've used this for years and have a folder with my entire drive backup'd up but not in an image so I can easily restore config files and such with ease. Here is the script I use:

sudo rdiff-backup -v 5 --exclude /sys --exclude /media --exclude /mnt --exclude /lost+found --exclude /proc --exclude /tmp / /mnt/backup/UbuntuBackups-$(date +%Y-%m-%d)/  

Here are the bench warmers: 

Mondo rescue: Very good program that makes bootable cd/dvds of your partition. 
Partimage: Great program, reliable and very popular

Now I can make secure backups and knowing so allows me to sleep safe at night ;)

---

### Post by klepto on 2008-10-25
Ok, 

I've been making many backups as I reinstalled Ubuntu to upgrade to Intrepid Ibex which I love btw. My two favorite backup apps are: 

[Image for Linux]("http://www.terabyteunlimited.com/image-for-linux.htm"), rock solid as you can verify bit per bit to make sure that the backup is perfect. It will also mount windows shares/samba/etc and it just is wonderful.

Sbackup, I love this program, nice gui so you can setup daily/weekly/etc backups with little to no effort and it does incremental backups as well. Here's a [nice tutorial]("http://maketecheasier.com/backing-up-data-in-ubuntu-using-sbackup/2007/12/08") for anyone who is interested

I use both of these.. there is a free tool for Image for Linux that allows you to mount your backup in Linux or Windows to grab what ever files you need.

---

