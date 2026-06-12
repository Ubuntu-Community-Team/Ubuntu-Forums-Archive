---
title: "Installation Freezes at 5%?"
date: 2009-08-30
forum: Installation &amp; Upgrades
---

### Post by MrParsons on 2009-08-30
I installed Ubuntu 9.04 on my personal Dell Laptop a few weeks ago, Installed it on my new PC yesterday, and now I am attempting to install it on my Acer work laptop. I know that it meets the specs(100gb HD, 1gb Ram) So Ive done the check disk and it says no errors, but everytime i go to install it, It hangs up on the "Installing system, Partitions Formatting, 5%, Creating ext3 file system for / in partition #1 of SCSI1 (0,0,..."

Everytime. Its driving me nuts. I deleted Windows off of it, and there is nothing on the hard drive now. What am I doing wrong??:(

---

### Post by tal007 on 2009-08-30
Just wiping it clean will not do. You have to make sure that you have large enough space on your drive unused, unpartitioned and not occupied by other OS like Xp Vista etc..

You may have 100 gb drive, but you probably have already allocated that to your previous OS. So, if Ubuntu sees it already allocated to other OS, it may hang during installation. You can wipe it clean, but the partition table still there in your MBR. So, you have to delete it from your MBR. 


This is how it looks like -

This area is 512 bytes and resides on the 1st sector of your hard drive.


-----------------------------
Some code

-----------------------------
partition  1    data 
------------- ----------------
partition  2    data
-----------------------------
partition  3    data
----------------------------
partition  4    data
----------------------------
Boot signature
-----------------------------


data = where partition starts and where it ends.


You have to delete your partition table from your MBR, so that Ubuntu does not see it as occupied by other OS.

You can use delpart.exe to delete it.
Bring up your system using a generic boot floppy ( generic win 98 or Dos ) and then delete your partition using delpart.exe. Then do the installation. You can find then on the internet.

Alternative :

First, try to delete partition using the Live Ubuntu CD. If it works, you don't have go through what I described earlier. Create  space large enough for Ubuntu installation. The space you have created must be left unused and unpartitioned. Then try it.

---

### Post by MrParsons on 2009-08-30
Alright, So I'm in GParted on the live CD, and I just deleted everything. I have "Unallocated 93.16GiB"

I restarted the laptop, and when to "Install Ubuntu"
Select "English" and the forward.
Select my city, then forward.
Leave Keyboard layout and forward.
I tried Use the largest Continuous free space first and it didnt work, froze at 5%
So now I restarted it, go back into gparted, and now it says
"/dev/sda1 (!) unknown 91.91gb"
"/dev/sda2 (keys) extended 1.23gb"
">>>>/dev/sda5 (keys) linux-swap 1.23gb"

So now Im r edoing it but this time i selected the option to select the drive instead

So im in the prepare partitions and have it setup like this

-/dev/sda
--/dev/sda2 ext3 /(mount point) (format checked)98695MB) unknown
--/dev/sda5 swap 1324MB unknown

what am i messing up :(

---

### Post by tal007 on 2009-08-30
Very puzzled. It happened to me last week. I could not installed  Ubuntu on my desktop computer. Just like you I tested everything and  found nothing wrong. But when I changed my Hard Drive everything worked great. In my case, it could be hard driver controller problem. That's what I am assuming. I read somewhere that it is hard to get Ubuntu working on all type of hard drives. I don't know Ubuntu's limitation. The author was explaining UDMA and system BIOS, how they fail to communicate. 

Try with a smaller unused space size like 10 GB or 15 GB. I don't know if it is having problem with the amount space you are giving to it.Also, check if your BIOS can access that size of space. Sometimes the amount of space BIOS and OS can access is different. They need to match.

---

