---
title: "partitions not detected"
date: 2009-05-30
forum: Installation &amp; Upgrades
---

### Post by dhawal_dhingra on 2009-05-30
today, I tried installing ubuntu 9.04 desktop edition along with XP. But by mistake,I inserted ubuntu 9.04 server edition CD and didnt notice till the installation was complete.
After that I thought of removing ubuntu server 9.04 from my PC so I booted XP and formated its partition along with swap partition. Then when I restarted my PC, it said something like- 
Loading Grub please wait.
Error 22

So I inserted Ubuntu Server 9.04 CD again to re-install it. But the problem was that it wasnt showing any previous partitions. I tried sudo grub and then find /boot/grub/stage1 it said-
ERROR 15: File Not Found
TO check my previious partitions, I tried sudo fdisk -lu but it said unable to seek on /dev/sda

can any one tell me how to resolve this??
what sould I do so that partioner detects my partitions?
I cant boot to XP even. I have to use live ubuntu 7.10 CD to use my PC.

---

### Post by merlinus on 2009-05-30
I would boot from your xp disk, and choose restore and fix mbr.  That way you will be able to access windows.

Then reinstall ubuntu.

Or you could simply try reinstalling ubuntu.  The grub error is because ubuntu no longer exists.

---

### Post by presence1960 on 2009-05-30
GRUB is gone you deleted the Ubuntu partitions, so of course when you ran those commands GRUB was not found. First you need to repair Windows bootloader see this : [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Then once you have windows running I would then proceed with the install of Ubuntu. My personal preference is to set up the partitions prior to install then use the manual option at the partitioner screen on the install. You can use the Ubuntu Live CD (System > Administration > Partition Editor) or the gparted Live CD to create your Ubuntu partitions prior to install.

---

### Post by Salmontarre on 2009-05-30
I think I'm having a similar issue [here.]("http://ubuntuforums.org/showpost.php?p=7372487&postcount=54")  There is another person with same problem [here,]("http://ubuntuforums.org/showthread.php?t=1171956") where that person has gotten a response.

I think we messed up by playing with ext3 partitions, which at least seems to be a common cause of a bunch of problems.

Argh

---

### Post by dhawal_dhingra on 2009-05-30
after repairing my XP bootloader, ubuntu installation will detect the previous partitions??

---

### Post by merlinus on 2009-05-30
Even if it does not, you can select where to install.  Be sure to select manual at the partitioning screen, and do not choose to use entire disk.

You also can opt to create a separate /home partition, so when upgrading or reinstalling, you will not lose application settings and such.

---

### Post by dhawal_dhingra on 2009-05-31
It is just showing my entire hard disk as single dev/sda 160 gb.
If I partition it to install ubuntu, my original data will be lost which i cant afford.
I will try to use XP disk today as I am downloading it now. If even that doesnt work, then I will back up all my data and format entire har disk.

---

