---
title: "Grub giving error 17"
date: 2008-12-03
forum: Installation &amp; Upgrades
---

### Post by RandomInfinity on 2008-12-03
After using gparted to format a partition that was not available, I got the following error
from Grub at startup.

error 17

I attemped to remove grub and reinstall it but could not reinstall since the manager was looking for grub at an internet site instead of on the Ubuntu CD I was using.  I still get the error so apparently uninstalling Grub did not remove it from the initial start of my computer.  I only have net access through dialup AOL so I can not get anything using ubuntu CD. 

I need help with doing one or more of the following: 

1.  some way to get grub(from Ubuntu 8.04) off my machine (Win XP Dell GX520) so I can start over?

2.   some way to get Grub downloaded and installed from a CD or Flash drive?

3.  reinstalling ubuntu from the CD over the existing space occupied by Ubuntu or instructions on how to remove Ubuntu so I can start over with a new install.  I tried an install but it wanted to use the new partition that I just formatted instead of replacing or updating the existing install.

4.  Correcting the error in Grub so it will function.

---

### Post by caljohnsmith on 2008-12-03
OK, how about booting your Live CD, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
```
One of the above commands should return your main Ubuntu partition (or /boot partition if you have one) in the form of (hdX,Y) where X and Y are numbers, for example (hd0,4), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Please post the output of all the above commands, reboot, and let me know if that corrects the problem.

---

### Post by RandomInfinity on 2008-12-05
> **caljohnsmith said:**
> OK, how about booting your Live CD, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
```
One of the above commands should return your main Ubuntu partition (or /boot partition if you have one) in the form of (hdX,Y) where X and Y are numbers, for example (hd0,4), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Please post the output of all the above commands, reboot, and let me know if that corrects the problem.
I did as you asked and got the following response

	 	  [ Minimal BASH-like line editing is supported.   For  
          the   first   word,  TAB  lists  possible  command  
          completions.  Anywhere else TAB lists the possible  
          completions of a device/filename. ]  
 

 grub> find /boot/grub/stage1  
 

 Error 15: File not found  
 

 grub>  find /grub/stage1  
 

 Error 15: File not found  
 

 grub>  
 
Since I did not find grub on the drive, is there some way to get it from the CD or to reinstall Ubuntu in the same space that it is in now?  Or maybe download grub and reinstall it from a flash drive?

---

### Post by caljohnsmith on 2008-12-05
Did you type "sudo grub" and not just "grub" to get the Grub command line? That could be why you are getting those "file not found" errors. How about posting:
```
sudo fdisk -lu
```
From the above output, determine which is your Ubuntu partition in the form sdXY (like sda2 or similar) by noticing which partition is "linux" under the "system" category, and then use that as follows:
```
sudo mount /dev/sdXY /mnt
ls -lR /mnt/boot
cat /mnt/boot/grub/menu.lst
```
And note the "-l" is a lowercase L, not a one. Please post the output of all the above commands and we can work from there.

---

### Post by RandomInfinity on 2008-12-06
> **caljohnsmith said:**
> Did you type "sudo grub" and not just "grub" to get the Grub command line? That could be why you are getting those "file not found" errors. How about posting:
```
sudo fdisk -lu
```From the above output, determine which is your Ubuntu partition in the form sdXY (like sda2 or similar) by noticing which partition is "linux" under the "system" category, and then use that as follows:
```
sudo mount /dev/sdXY /mnt
ls -lR /mnt/boot
cat /mnt/boot/grub/menu.lst
```And note the "-l" is a lowercase L, not a one. Please post the output of all the above commands and we can work from there.

I made sure I used sudo grub and I got the same as shown previously.

I folowed your instructions and here is the results.  The only linux that showed up was the swap area so I repeated the mount for each directory as you will see below.  I can still access all my drives and partitions using the live CD.  The folders seem to be intact.  I still can not get pass the Grub start to get to windows or ubuntu.

	 	 ubuntu@ubuntu:~$ sudo fdisk -lu  
 


 Disk /dev/sda: 80.0 GB, 80000000000 bytes  
 255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors  
 Units = sectors of 1 * 512 = 512 bytes  
 Disk identifier: 0x41ab2316  
 


    Device Boot      Start         End      Blocks   Id  System  
 /dev/sda1              63       64259       32098+  de  Dell Utility  
 /dev/sda2   *       64260   156216059    78075900    7  HPFS/NTFS  
 


 Disk /dev/sdb: 80.0 GB, 80000000000 bytes  
 255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors  
 Units = sectors of 1 * 512 = 512 bytes  
 Disk identifier: 0x00000081  
 


    Device Boot      Start         End      Blocks   Id  System  
 /dev/sdb1              63    22748039    11373988+   7  HPFS/NTFS  
 /dev/sdb2        22748040   156248189    66750075    5  Extended  
 /dev/sdb5        22748103    23985044      618471    7  HPFS/NTFS  
 /dev/sdb6       150705828   156248189     2771181   82  Linux swap / Solaris  
 


 Disk /dev/sdc: 128 MB, 128450560 bytes  
  	 	 16 heads, 32 sectors/track, 490 cylinders, total 250880 sectors  
 Units = sectors of 1 * 512 = 512 bytes  
 Disk identifier: 0x00000000  
 


    Device Boot      Start         End      Blocks   Id  System  
 /dev/sdc1   *          32      250879      125424    6  FAT16  
 ubuntu@ubuntu:~$ 
 ubuntu@ubuntu:~$ sudo mount /dev/sdb6 /mnt  
 /dev/sdb6 looks like swapspace - not mounted  
 mount: you must specify the filesystem type  
 ubuntu@ubuntu:~$ 
 ubuntu@ubuntu:~$ ls -lR /mnt/boot  
 ls: cannot access /mnt/boot: No such file or directory  
 ubuntu@ubuntu:~$ 
 ubuntu@ubuntu:~$ sudo mount /dev/sdb2 /mnt  
 mount: you must specify the filesystem type  
 ubuntu@ubuntu:~$ 
 ubuntu@ubuntu:~$ sudo mount /dev/sdb5 /mnt  
 ubuntu@ubuntu:~$ ls -lR /mnt/boot  
 ls: cannot access /mnt/boot: No such file or directory  
 ubuntu@ubuntu:~$ 
 ubuntu@ubuntu:~$ ls -lR /mnt/boot  
 ls: cannot access /mnt/boot: No such file or directory  
 ubuntu@ubuntu:~$ 
 ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt  
 ubuntu@ubuntu:~$ ls -lR /mnt/boot  
 ls: cannot access /mnt/boot: No such file or directory  
 ubuntu@ubuntu:~$

---

### Post by caljohnsmith on 2008-12-06
According to your fdisk output, you don't have any linux partitions; did you try to install Ubuntu to the NTFS partition sdb5? If so, you need to install Ubuntu to a partition that uses a linux file system like ext3 for example. NTFS won't work for Linux because it can't handle permission/ownership metadata for instance. How about reinstalling Ubuntu, but first open gparted (System > Admin > Partition Editor) to reformat whichever partition you want for Ubuntu to use ext3. Also, when you go through the Ubuntu installer, I would recommend clicking the "advanced" button near the end of the installation, and specify to have Grub installed to /dev/sdb since that is the drive you are installing Ubuntu to. Then if all goes well and the installation completes successfully, reboot, and go into your BIOS and specify the sdb Ubuntu drive as first in the boot order. Then you should be able to boot Ubuntu with no problems if all goes well. Let me know how it goes. :)

---

### Post by RandomInfinity on 2008-12-07
> **caljohnsmith said:**
> According to your fdisk output, you don't have any linux partitions; did you try to install Ubuntu to the NTFS partition sdb5? If so, you need to install Ubuntu to a partition that uses a linux file system like ext3 for example. NTFS won't work for Linux because it can't handle permission/ownership metadata for instance. How about reinstalling Ubuntu, but first open gparted (System > Admin > Partition Editor) to reformat whichever partition you want for Ubuntu to use ext3. Also, when you go through the Ubuntu installer, I would recommend clicking the "advanced" button near the end of the installation, and specify to have Grub installed to /dev/sdb since that is the drive you are installing Ubuntu to. Then if all goes well and the installation completes successfully, reboot, and go into your BIOS and specify the sdb Ubuntu drive as first in the boot order. Then you should be able to boot Ubuntu with no problems if all goes well. Let me know how it goes. :)

Before I start the reinstall, I am on a windows XP machine.  I have a few questions 

1.  How do I determine which drive is sdb in the bios?  Do the a and b designations correspond to the A and B drives in the bios?

Ubuntu worked initially for me as did Grub.  Grub stopped working when I partitioned a section that was made unusable at my initial installation of Ubuntu.  All of the ubuntu files are on the machine.  

I also would not want to accidently put Ubuntu over my existing data files. 

2.  How can I look at the contents of each partition to make sure that I do not copy over or in some other way destroy my existing data files and specify where ubuntu is to be installed?

3.  Is there a sudo dir command or some other command to check the contents of each partition before I start the new install?

---

### Post by caljohnsmith on 2008-12-07
> **RandomInfinity said:**
> Before I start the reinstall, I am on a windows XP machine.  I have a few questions 

1.  How do I determine which drive is sdb in the bios?  Do the a and b designations correspond to the A and B drives in the bios?

Unfortunately, no, the A and B drives in BIOS do not necessarily correspond to sda and sdb respectively, although they can. Usually the best way to tell is by comparing the drive sizes, and also compare the manufacturer of the drive if that info is listed in BIOS. 
> **RandomInfinity said:**
> 
Ubuntu worked initially for me as did Grub.  Grub stopped working when I partitioned a section that was made unusable at my initial installation of Ubuntu.  All of the ubuntu files are on the machine.  

I also would not want to accidently put Ubuntu over my existing data files. 

2.  How can I look at the contents of each partition to make sure that I do not copy over or in some other way destroy my existing data files and specify where ubuntu is to be installed?

3.  Is there a sudo dir command or some other command to check the contents of each partition before I start the new install?
Did you install Ubuntu using the "Install Ubuntu" option from the main menu of the Ubuntu Live CD? Or did you choose "try Ubuntu without making changes", boot to the desktop, and then double-click the Ubuntu installer icon on the desktop? It sounds like you might have installed Ubuntu via the first case, which is a "Wubi" install, meaning you install Ubuntu inside of Windows, or on another NTFS/FAT partition. How about posting the following so we can see what is in your partitions:
```
sudo mkdir /mnt/sda2 /mnt/sdb1 /mnt/sdb5
sudo mount /dev/sda2 /mnt/sda2
sudo mount /dev/sdb1 /mnt/sdb1
sudo mount /dev/sdb5 /mnt/sdb5
ls -l /mnt/sda2 /mnt/sdb1 /mnt/sdb5
```
And note "-l" is a lowercase L, not a one. That should help clarify what your setup is, and whether you did a Wubi install.

---

### Post by RandomInfinity on 2008-12-12
Thanks for showing me how to look at the files on the partitions.  I looked through the lists and apparently I succeeded in eliminating the Ubuntu install after all.  Obviously I know just enough to ge myself into trouble.

sdb5 and sdb1 have my data files.  sda2 has some of my C drive material and sda1 has my windows operating system.   No ubuntu material on any of these.  So, I guess I need to reinstall Ubuntu

The first time I used the install program on the CD.

Can I use that again?
How do I make sure that it installs in the unused areas of the drive?

---

