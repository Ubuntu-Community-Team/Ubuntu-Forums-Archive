---
title: "Where's Grub installed to?"
date: 2009-03-25
forum: Installation &amp; Upgrades
---

### Post by starman38 on 2009-03-25
I'm trying to install ubuntu 8.10.  Again.  I have 2 internal sata hds and 1 ide hd partitioned fat32, bootit, linux ext3, and linux swap, in that order according to bootit partition program.  They are all primaries (not sure about the swap file, but there is no more than 4).  I use the 3rd party boot manager BootitNG and it has done the job on Feisty Fawn and xp.

I can't figure out what partition (or just plain Where?) grub is installing.  The Bootit partition tool shows hd0 as my first hd and the one with xp on the first partition.  The bootit partition is next,and the linux partition /(root) is the third.  The linux swap is fourth.

When I installed from the alternate cd, the partition program (not sure which is on that cd), named my only ide drive as scsi3, sdc.  My other two sata drives are scsi1 and scsi2.  Why is the ide drive third behind my 2 satas and how do I specify the location to install grub to my root partition?

---

### Post by meierfra. on 2009-03-25
> Why is the ide drive third behind my 2 sata
Ubuntu used  to use different drivers for ide and sata drives. As a result the ide drives were called hd? and the sata drive sd?, and the ide drive were always listed before the sata drive. By now Ubuntu uses the same drivers for all hard disk,   all  hard disks are  called sd?, and  an ide drive maybe listed after a sata drive.


> how do I specify the location to install grub to my root partition? 

The alternate cd will asked you whether Grub should be installed to the MBR. If you say "no", you can choose which partition Grub should be installed to. Just choose your ubuntu root  partition, which seems to be /dev/sdc3.

If you use the LiveCD,  click on the "advanced" button in the last step of the installation and  you will be able to choose the location for grub.

---

### Post by starman38 on 2009-03-26
Thanks for the informative reply.  I haven't been able to use the live cd for the install because my video is not supported.  I've got an ati 9600 radeon card which works fine with the Feisty Fawn but not the live cd. I will try again.

---

