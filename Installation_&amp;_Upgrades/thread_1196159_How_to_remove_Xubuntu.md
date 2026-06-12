---
title: "How to remove Xubuntu?"
date: 2009-06-24
forum: Installation &amp; Upgrades
---

### Post by xubunted on 2009-06-24
Hi all!

I was rather rash in installing Xubuntu on an old computer. I was really eager to discover Linux and wasn't careful enough during installation. I did make sure Linux didn't overrun Windows, so I can still use the latter. My problem is that I'm not really sure where I installed Xubuntu. The C: drive on this computer is almost completely full and I had cleaned D: drive in hope Linux would get installed there. Well it didn't. I have no idea where it is (installed, that is). When I try to download upgrades for Xubuntu, approximately 128 Mb, I get a notice that there is not enough space available (yet D: drive has around 10 Gb of space - so I guess that confirms it can't be there).

Anyway, now I would like to remove Xubuntu completely from wherever it is and reinstall it on D: drive (or better yet, a part of D: drive). Then I could progressively get to know the OS, by installing new programs (which I understand is not as automatic as in Windows).

I did some research concerning Linux removal. I have to admit I don't really have a clue about partitioning and that is also why I am asking my question on this forum (otherwise I guess I would understand the solutions already proposed elsewhere).

One solution I did find and try out was to make a Ultimate Boot CD and to do something complicated with it after restarting my computer :). I did so, but in one of the last steps, where I was supposed to boot from Windows partition (to remove Linux?), I didn't know which partition to chose (I'm not even sure the menu was displaying partitions, I could choose between UMBPCI and EMM386, whatever they are).

I think it is perfectly clear I'm clueless about what I'm doing and I would really appreciate if someone could help me with this issue.

I'm rather desperate here. Normally I manage to fix my problems by googling computing forums, but this time I couldn't make any use of what I found. It's just too many new things at once, I guess.

---

### Post by presence1960 on 2009-06-24
if you can boot xubuntu do so or boot the xubuntu Live CD. Open a terminal and run this command ```
sudo fdisk -l
``` BTW that is a lowercase L. post the output here. We'll see where it is installed.

BTW Linux doesn't use the nomenclature of C: , D: , E; , etc for drives. Try not to use that here so communication can be clear. Your first disk is sda, then next disk is sdb (if you have another hard disk) partitions on your first disk are expressed like this sda1 is your first partition on the first disk, sda2 is the second partition on your first disk, etc. With Windows C: can be on your first disk and D: can be on an altogether different physical disk. So those letter descriptions are of no use here.

---

### Post by xubunted on 2009-06-25
First of all, thank you for taking your time to consider my post.

I did as you suggested and here is the result (in a weird mixture of English and Slovene):

> Disk /dev/sda: 41.1 GB, 41174138880 bajtov
255 heads, 63 sectors/track, 5005 cylinders
Units = steze of 16065 * 512 = 8225280 bytes
Disk identifier: 0x92a492a4

  Naprava Zagon    Za&#269;etek       Konec     Bloki    Id  Sistem
/dev/sda1   *           1        1054     8466223+   7  HPFS/NTFS
/dev/sda2            1055        5005    31736407+   f  W95 Razš'a (LBA)
/dev/sda5            1055        4679    29117781    b  W95 FAT32
/dev/sda6            4680        4983     2441848+  83  Linux
/dev/sda7            4984        5005      176683+  82  Linux izmenjalni / Solaris


I guess I only have one HD (just learned something new). Hum, how do I remove Linux and reinstall it so it will have enough space for as many updates and programs as possible?

---

### Post by presence1960 on 2009-06-25
well you definitely do not have enough space allocated for the xubuntu partition. I would first back up all my data. Then defrag windows at least once or twice. Then you are going to have to use the xubuntu Live CD by booting off the CD and choosing "Use Ubuntu without any changes". When the desktop loads go System > Administration > Partition Editor. First remove the Linux partitions and then the extended partition they are contained in to create unallocated space.. Next you are going to resize the windows partition to create more unallocated space. Very important here that you have already defragged windows!. Once you have completed this you can now create your xubuntu partitions from your unallocated space. When completed you can install. When you get to the Prepare disk space window of the install process choose the manual option. you will then highlight your intended partitions one at a time and set parameters for each one by clicking Edit partition. Set partition type (primary, extended or logical), Use as (choose file system ext3 or ext4) mountpoint ( "/" for root, "/home" if you create a separate home partition).

I would suggest that you read and become fully acquainted with the partitioning/installationation process before attempting to do it. Here are a few links to get you started:

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)  -for a free pdf Ubuntu Pocket Guide which BTW has a great step by step how to on the installation process.

Setting up a new OS is no small undertaking especially if you have never done it before- but it can be done right if prepared for the task. Restoring windows from a recovery CD/DVD or recovery partition is not the same thing since it auto partitions your drive(s) and installs all drivers for you. Using a Windows install CD/DVD is setting up a new OS as using that CD you must choose your partition scheme, have the option of creating/deleting partitions and you must find/install all drivers.

Good luck and if you have any questions post back here. We will be glad to help.

---

### Post by xubunted on 2009-06-25
Thank you very much for the detailed instructions and useful links. I'm guessing it will take me several days to understand all what needs to be understood in order to put everything in the right place. I better get started right away.

P.S.
Will report about my success.

---

### Post by raymondh on 2009-06-25
Just out of curiosity, what are the specs of your system?

---

### Post by xubunted on 2009-06-26
Memory: 245,0 MiB
Processor: Intel Celeron 1200MHz
HD: 40 GiB

---

### Post by xubunted on 2009-06-26
I quickly went through the Ubuntu Pocket Guide, studied the first link (partitioning) you (presence1960) gave me and had a glance at the second (graphical install).

Here is what I did.

I deleted the extended partition. I resized Windows partition to 18 Gb, I created a new extended partition and a new local partition and formated it with ext3 filesystem (500 Mb of it was already used, which surprized me somewhat, since I had created this partition out of scratch so to speak).

Anyway, then I went on to reinstall Linux. Sadly, Linux didn't choose the logical partition (sda5) to install itself, instead it created two new small logical partitions, sda6 and sda7 (again!).

Since sda5 already contained 500 Mb of some data, I resized it to 2 Gb, then I moved sda6 (with Linux on it) and resized it to 16 Gb, while I couldn't change anything in sda7 - Linux-swap partition (which remains rather small, only some 100 and something Mb).

It doesn't look pretty, but it should function, right? I was able to download and install all the updates available. Sadly, Youtube, Dailymotion and alike don't function very well ... (even with Flash player and other stuff installed). I also have some problem with my display setting, Linux won't save the resolution and refresh rate I choose, so everytime I restart the computer I'm offered a resolution I don't want. But I guess those are problems to be asked in other portions of the forum.

P.S.
I wonder how often can one make changes in partitions (resize, move, delete, create) and not harm the hard disk?

---

### Post by presence1960 on 2009-06-26
> **xubunted said:**
> I quickly went through the Ubuntu Pocket Guide, studied the first link (partitioning) you (presence1960) gave me and had a glance at the second (graphical install).

Here is what I did.

I deleted the extended partition. I resized Windows partition to 18 Gb, I created a new extended partition and a new local partition and formated it with ext3 filesystem (500 Mb of it was already used, which surprized me somewhat, since I had created this partition out of scratch so to speak).

Anyway, then I went on to reinstall Linux. Sadly, Linux didn't choose the logical partition (sda5) to install itself, instead it created two new small logical partitions, sda6 and sda7 (again!).

Since sda5 already contained 500 Mb of some data, I resized it to 2 Gb, then I moved sda6 (with Linux on it) and resized it to 16 Gb, while I couldn't change anything in sda7 - Linux-swap partition (which remains rather small, only some 100 and something Mb).

It doesn't look pretty, but it should function, right? I was able to download and install all the updates available. Sadly, Youtube, Dailymotion and alike don't function very well ... (even with Flash player and other stuff installed). I also have some problem with my display setting, Linux won't save the resolution and refresh rate I choose, so everytime I restart the computer I'm offered a resolution I don't want. But I guess those are problems to be asked in other portions of the forum.

P.S.
I wonder how often can one make changes in partitions (resize, move, delete, create) and not harm the hard disk?

At the prepare disk space window of the installer did you choose "manual"? you must choose manual to "manually" select the partitions you want to use rather than have the installer select them. here is a shot of the prepare disk space window:

---

### Post by presence1960 on 2009-06-26
partitioning will not harm your hard disk.

---

### Post by xubunted on 2009-06-30
Thank you very much for all your help, presence1960.

Since I was last here, I also moved and resized Linux-swap partition.

On this forum I was also able to find the answers to the other two problems (resolution, video sites), so Linux is working smoothly now.

---

### Post by presence1960 on 2009-06-30
> **xubunted said:**
> Thank you very much for all your help, presence1960.

Since I was last here, I also moved and resized Linux-swap partition.

On this forum I was also able to find the answers to the other two problems (resolution, video sites), so Linux is working smoothly now.

Glad you got it working. Enjoy Ubuntu!

---

