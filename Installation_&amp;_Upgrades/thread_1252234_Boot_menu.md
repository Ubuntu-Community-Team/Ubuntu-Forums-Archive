---
title: "Boot menu"
date: 2009-08-28
forum: Installation &amp; Upgrades
---

### Post by loosescrew on 2009-08-28
I will try to keep this short. I had ubuntu 9.04 installed within windows xp. I liked it so I decided to install 2nd hard drive for ubuntu.Installation went smoothly. The problem I have is-
on the first screen (boot screen) that comes up, i'm prompted to choose operating system to boot to.
ubuntu 9.04,kernel 2.6.28-15-generic
          ubuntu 9.04,kernel 2.6.28-15-generic (recovery mode)
          ubuntu 9.04,kernel 2.6.28-11-generic
          ubunut 9.04,kernel 2.6.28-11-generic (recovery mode)
          ubuntu 9.04,memtest 86+
                       other operating systems
                       windows nt/2000/xp
                       ubuntu 
Why two ubuntu's with differant kernals.
Also, under other operating systems, the windows nt/ 2000/ xp boots to the recovery console. How do I change ubuntu (under other operating systems to show windows xp ? When you select ubuntu (under other operating systems) you boot into windows xp. I edited the boot.ini file so that it no longer shows ubuntu. So i'm assuming it has to be fixed with the grub loader. I apologize if this is hard to understand. Thanks, Joe

---

### Post by stlsaint on 2009-08-28
there is gonna be another guy posting who will assist this much further...hopefully(presence) but how are your hdd setup right now since you say you added a new hdd and then re-installed Grub...just strictly based off what you are saying you had a dual boot hdd then added another hdd for ubuntu..correct? did you change all this in Grub as well to tell Grub what to do with the previous ubuntu partition? post the results of 
sudo fdisk -l

---

### Post by stlsaint on 2009-08-28
> **loosescrew said:**
> I will try to keep this short. I had ubuntu 9.04 installed within windows xp. I liked it so I decided to install 2nd hard drive for ubuntu.Installation went smoothly. The problem I have is-
on the first screen (boot screen) that comes up, i'm prompted to choose operating system to boot to.
ubuntu 9.04,kernel 2.6.28-15-generic
          ubuntu 9.04,kernel 2.6.28-15-generic (recovery mode)
          ubuntu 9.04,kernel 2.6.28-11-generic
          ubunut 9.04,kernel 2.6.28-11-generic (recovery mode)
          ubuntu 9.04,memtest 86+
                       other operating systems
                       windows nt/2000/xp
                       ubuntu 
Why two ubuntu's with differant kernals.
Also, under other operating systems, the windows nt/ 2000/ xp boots to the recovery console. How do I change ubuntu (under other operating systems to show windows xp ? When you select ubuntu (under other operating systems) you boot into windows xp. I edited the boot.ini file so that it no longer shows ubuntu. So i'm assuming it has to be fixed with the grub loader. I apologize if this is hard to understand. Thanks, Joe


also the multiple kernels can be edit as well thru menu.lst...just fyi...

---

### Post by loosescrew on 2009-08-28
Thanks, stsaint,
I installed ubuntu with wubi into windows. It was installed, when i installed ubuntu to second hard drive. During install I was asked which drive to install ubuntu on.I selected the hard drive I just installed and had ubuntu use the whole drive.
I'm not sure what you mean how are the hard drives set up. One is listed as hdd(0) main drive(master) with windows
2nd is listed as hdd(1) slave drive with ubuntu. I believe !

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdad4f39a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         473     3799341    b  W95 FAT32
/dev/sda2   *         474        9728    74340787+   7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x267ee1c6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9461    75995451   83  Linux
/dev/sdb2            9462        9729     2152710    5  Extended
/dev/sdb5            9462        9729     2152678+  82  Linux swap / Solaris
 
I don't recall grub asking anything about the windows/ubuntu partitions.AFTER, I selected the new drive.. Thanks Joe

---

### Post by loosescrew on 2009-08-28
stlsaint, This problem is solved. I edited the  menu.lst.. Everything is listed as it should be. Thank You, Joe

---

### Post by stlsaint on 2009-08-28
Great sorry for late help...go busy!!

---

### Post by oldfred on 2009-08-28
Presence always does it correctly by asking for complete info before suggesting corrections. He would ask for you to download and run this script and post the results.txt file it makes so we can make correct assumptions for corrections:
Boot Info Script 0.32 courtesy of forum member meierfra
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

But I think I have enough info to guess you corrections.[IMG]http://ubuntuforums.org/images/icons/icon7.gif[/IMG] Try at your own risk.
Make a copy of your menu.lst just in case.
sudo cp /boot/grub/menu.lst  /boot/grub/menu.lst.backup

then we will edit your menu.lst
gksudo gedit /boot/grub/menu.lst

At the bottom you have your windows nt/2000/xp stanza. put # signs at the beginning of the lines to comment them out since they point to your recovery partition. probably (hd0,0)
Edit the next line just to change the title to look like below, If the additonal lines in yours are not identical but work do not change the other lines. ( this is my entry except mine is (hd0,0) )

title Microsoft Windows XP Professional
rootnoverify (hd0,[COLOR=Black]1[/COLOR])
savedefault
chainloader +1

Also in menu.lst are commands to limit the number of ubuntus to show. change this line:

howmany=2

---

### Post by loosescrew on 2009-08-28
Thanks oldfred, I appreciate the reply. I did as you suggested. I will reboot to see how things turned out. Thanks Joe

---

