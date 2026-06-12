---
title: "How should I partition my new SSD?"
date: 2018-06-05
forum: Hardware
---

### Post by SagaciousKJB on 2018-06-05
I got a 480 GB SSD drive for free the other day, and before I just pop it into the computer, I wanted to ask some things to make sure I'm utilizing it the best way.

First of all, no swap or swap?  I've heard that the amount of page writes will quickly diminish the life of the SSD as they have a limited amount of "writes".  On the other hand, I only have 4 GB of ram ( never thought I'd see the day where I'd be saying 'only 4GB of ram ' ) so having quicker swap would be nice.

Well, with that in mind, if I wanted to avoid excess writes, then what about things like /var/, or the '.' directories in my home folder? Don't those also have excessive writes to them during normal operation?

I don't often reboot my computer, so the increased boot speed isn't really a big factor of appeal, but I thought it might speed up my computer in other ways to have the root partition on it?

In any case, it's also just a lot of storage space so I want to use some of that for storing things like media.  I do a lot of DVR recording, DVD ripping, that sort of thing, so having an extra 480 GB helps, but I don't want to waste the speed benefit.

Anyway, so I'm thinking that a good partioning scheme for this would look something like...

Partition 1 have...
/boot/
/etc/
/opt/
/usr/
 
Partition 2 have...

/mnt/storage/

Then I will have /home/, /var/, /proc/, /tmp/, etc. on HDDs.

But I guess the real question is, will putting /boot/, /etc/, /opt/, and /usr/ on the SSD really increase speed on the system on anything besides the boot time?

---

### Post by oldfred on 2018-06-05
I keep all of / (root) on SSD including /home. But my /home is just about only the hidden files & folders. All data is in a /mnt/data partition on HDD and linked back into /home so it looks like typical system, but folders are links.
Loading files is also quicker, particularly larger programs.

If you have 4GB of RAM, you probably do not need swap. New installs now use swap file of 2GB.
My system right now is using about 2GB of RAM. And most of the time it has more use, it is just older apps that I had used, but have not been overwritten with something new, yet.

Even swap on SSD is orders of magnitude slower than RAM. If running some application like video editing that fills RAM and starts using swap, time to get more RAM.

Is system UEFI or BIOS?
Will drive ever be installed in newer UEFI system? If so use gpt now and include both ESP - efi system partition and if now BIOS include bios_grub partition.

---

### Post by SagaciousKJB on 2018-06-08
It will be going into a BIOS system, but maybe in the future a UEFI.  Honestly I have no idea what UEFI is except it's different from BIOS.  So will I need to do something special to boot off the SSD with a BIOS system? The part about gpt and ESP was completely foreign to me.

So the frequent writes from things like /tmp/ or /var/, and the various '.' directories in /home/ won't degrade the drive faster?

Right now I also have most data on separate partitions similarly to you with /root/ on one drive, but then I just put /home/ on another, and have a few other drives I load into /media/

---

### Post by oldfred on 2018-06-08
If system if BIOS, then you can use MBR.

Its just that UEFI essentially requires gpt. And with Ubuntu you can use gpt with BIOS boot. Windows has to be MBR for BIOS boot.  I converted my BIOS system to boot Ubuntu from a gpt drive in 2010 and still had XP on MBR drive. Since then all new or reformatted drives are gpt.
With gpt and BIOS, you have to add one extra partition for grub to install correctly. It is 1 or 2MB unformatted with bios_grub flag. With UEFI you have to have the ESP - efi system partition which is FAT32 with boot flag. 
Even when still configuring new drives for my BIOS system and Windows 8 came out in 2012 and had to be UEFI on gpt, I started to add both bios_grub and ESP to all drives. I figured eventually I would get an UEFI system and might want drives to be able to boot on new system.

With SSD, you want to use noatime, so every access is not a write. On HDD I change from defaults to relatime to mount partitions. See man mount for details on mount options.

       [http://arstechnica.com/gadgets/2015/04/27/ask-ars-my-ssd-does-garbage-collection-so-i-dont-need-trim-right/](http://arstechnica.com/gadgets/2015/04/27/ask-ars-my-ssd-does-garbage-collection-so-i-dont-need-trim-right/)
Do SSD need customization?
[http://ubuntuforums.org/showthread.php?t=1981478](http://ubuntuforums.org/showthread.php?t=1981478)
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)
[https://wiki.debian.org/SSDOptimization](https://wiki.debian.org/SSDOptimization)
[http://ubuntuforums.org/showthread.php?t=2003022](http://ubuntuforums.org/showthread.php?t=2003022)
Similar to what I do, except I do use ext4 , I use a daily cron task for TRIM, 
and I have Firefox on hard drive so no issues with cache. Swap is also on hard drive, but never used.
[https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd)

---

### Post by SagaciousKJB on 2018-08-21
Thanks fred.

I finally got it put in yesterday, been pretty busy.  I made the changes to fstab options, changed the I/O scheduler and set up /tmp/ on a tmpfs.

I'm still not really sure how about things like ~/.cache or /var/ though.  From what I've read, even though some places in /var/ are not supposed to be persistent over boots, some distributions expect them to be, so I think I'll leave /var/ alone.  But how much does something like ~/.cache really write to the disk and should I worry about it?

---

