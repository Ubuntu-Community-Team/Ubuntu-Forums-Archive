---
title: "need help setting up a linux mini-itx file server"
date: 2009-05-28
forum: Installation &amp; Upgrades
---

### Post by xsk3l3t0rx on 2009-05-28
hi, i am looking to assemble a mini-itx media server in my house so that i can stream videos across my private LAN. this computer will consist of two identical 1TB SATA hdd's. 

*my build will consist of 
- a zotac GF9300-D-E LGA 775 motherboard
- intel pentium E5200 wolfdale 2.5 GHz cpu
- g. skill 2GB RAM (2x1GB) DDR2800

   what i want to do is run ubuntu 9.04 completely from a usb stick, and have the two hard drives contain ONLY multimedia (videos, pictures, music). I want anything important to the OS to be stored on the flash drive. 
   my question is, how would i go about setting up the flash drive? can anyone link me to a tutorial that will allow me to run the OS completely from the flash drive AND allow me to save changes directly to the drive, (like bookmarks, settings, yada yada). I guess what im saying is i want my /home folder to be spread across the two hdd's, or unless anyone else has a better idea (like possibly a RAID for data redundancy). im not a complete retard, but wen it comes to linux, i sure am. thanks all.

* ALSO: WHAT IS THE MAX SUPPORTED AMOUNT OF RAM BY UBUNTU?

---

### Post by lolobu on 2009-06-01
To run Ubuntu from a USB flash memory, you can have a look here :
[http://www.pendrivelinux.com/]("http://www.pendrivelinux.com/")

Regarding memory, up to 4GB (well it will use something like 3.5GB) on a 32 bits version. If you want more, you have to use the 64 bits version.

---

### Post by QuinnHarris on 2009-06-01
If you want to use all the capacity of the two drives (instead of use them for redundancy) I would strip (RAID 0) the drives.  But why boot from USB?  You could mirror 5GB of the drives for the OS and strip the rest.  The system will still work if one of the drives fails (you will lose the media partition) and you avoid the hassle and minor cost of the USB drive most notably the thing getting pulled.  You only loose 0.5% of the space.  Avoid the Nvidia RAID.  Its only worthwhile when Windows is involved.  The Linux RAID doesn't need specific hardware, supports more complex configurations, does a better job idiot checking and probably performs better.

Use the alternative CD as the normal CD doesn't expose any of RAID/LVM  features.  I honestly haven't used the Ubuntu Alternative CD recently but it believe its still based on the full Debian installer which has more options than you will ever want.

If you have never done this you will have to fiddle with the installer a bit before you get the jist of the whole thing.  I suggest trying to set it up as follows.
Partition the two drives identically with a 5-10GB partition and another partition using the remainder of the drive. Then setup MD (multi disk for RAID) with RAID 1 (mirror) for the small system partition and RAID 0 (strip) for the large media partition.  Then format the md with Ext4 or reiserfs for the large partition because they support file extents for faster large files operations.  You can also use LVM (Logical Volume management) probably on top of the big partition.  This can be very advantageous if you plan to add more drives sometime in the future and expand the existing file system to use the new drive.

That motherboard and processor is probably overkill for your task.  The processor might be good if you are ripping and converting DVD's but I really don't think you need close to that to watch even 1080p video.  I am not sure how well the transcoding software (handbreak?) is able to parallelize but if it scales well I expect you will get more rip per dollar from an AMD 3 or 4 core product (AMD Phenom 8650).  Highly scalable parallelized apps is the only place current AMD products offer a compelling value over Intel, and DVD ripping could be one of those few applications, but I am having trouble finding specific benchmarks.  But the E5200 is probably the best overall deal today.

You are paying a significant premium for MiniITX over MicroATX.  Is the smaller size worth it?  The extra SATA ports on most MicroATX could come  in handy for future upgrades.

---

### Post by p388l3s on 2009-06-01
No-one else seems to have mentioned it so I will....


instead of re-inventing the wheel why not try freenas it'll do everything you want without having to try and do it all yourself, you can also try openfiler, but so far i'm not too crazy about it.

Freenas is bsd based but so far it has done everything I've wanted it to do.

---

