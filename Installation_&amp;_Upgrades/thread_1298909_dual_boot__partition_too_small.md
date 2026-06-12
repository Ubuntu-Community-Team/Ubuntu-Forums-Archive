---
title: "dual boot  partition too small"
date: 2009-10-23
forum: Installation &amp; Upgrades
---

### Post by bigtone86 on 2009-10-23
I am currently running a dual boot xp pro/ubuntu 9.04. The problem I am having is that when I installed ubuntu I did not allowed myself enough hard drive space to run ubuntu effectively, ie 3.7gb out of a possible 120gb.
Its now got to the point where I can't even do important security updates. I was wondering if it's possible to reinstall ubuntu and create another partition without having to do a complete hd format and starting over.  Thanks in advance for any help

---

### Post by presence1960 on 2009-10-23
> **bigtone86 said:**
> I am currently running a dual boot xp pro/ubuntu 9.04. The problem I am having is that when I installed ubuntu I did not allowed myself enough hard drive space to run ubuntu effectively, ie 3.7gb out of a possible 120gb.
Its now got to the point where I can't even do important security updates. I was wondering if it's possible to reinstall ubuntu and create another partition without having to do a complete hd format and starting over.  Thanks in advance for any help

boot the Ubuntu Live CD, choose "try ubuntu without any changes", when the desktop loads go System > Administration > Partition Editor or open a terminal and run ```
gksu gparted
``` to open partition Editor.

You want to resize your XP partition by choosing resize and shrinking it the amount of space you want to add to Ubuntu. Get that set and click the grreen check mark (Apply) at the top. It may take a while to complete do not interrupt or stop the process.

When complete highlight your Ubuntu partition and use the resize process to add that space you just freed up to Ubuntu's partition. Again do not interrupt the process and allow it to complete.

When you resize each partition you will be presented with a graphic of that partition. Grab the end of the partition and move it with your mouse in the appropriate direction to shrink or grow the partition.

---

### Post by oldfred on 2009-10-23
+1 on presence's recommendations

Housecleaning XP and running defrag twice will help make space to expand Ubuntu partitions. Windows needs at least 20% free space to work well.

If you want to see graphical examples of gparted.
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by bigtone86 on 2009-10-24
** Worked a treat guys, give yourself a big pat on the back. I have learned a lot about partitions today**. **Many thanks to you both** .........**Bigtone** :guitar:

---

### Post by deepakp on 2009-10-24
thanks man! even i had the same problem!:KS

---

### Post by presence1960 on 2009-10-24
Glad you got it working! Enjoy Ubuntu.

---

### Post by atirox on 2009-10-25
Okay, so i have the same problem, but with a 40 GB HDD. Its in a Compaq Presario R3055CA. 

Anyway, I already have a partition manager in windows. However, the partition manager tells me that it cant alter the size of the disk, because it is used to boot the system. It tells me that i'd need to reconfigure GRUB after i resize the partition. My question is, Does GParted reconfigure Grub, or do I have to do that myself? If I have to do it myself, which is easier, using the partition manager i have in windows, or using GParted? 

Just as a little history behind why I ask, I love this laptop. Its 6 years old. One thing i love best about it is the Broadcom wireless card. It works wonders under windows. If most of you recall, Broadcom doesnt have any open source drivers, especially for the BCM43xx series, which was popular around the time that this machine was made. so i spent a good 3 hours trying to get the stupid thing to work, and I finally got it working. I'd rather not loose all the work i did trying to get the wireless card to work, which is why I don't want to just wipe the partition and reinstall it.

---

### Post by oldfred on 2009-10-25
atirox, you should start your own thread so that people using search engines can find the right question and answers.

Vista and later seem to be the only systems that allow you to edit the partitions while running. gparted needs to be loaded from the live CD so no partitions are mounted. If you have XP you should have not problems using Gparted. Of course always backup important data just in case. Gparted will not reinstall grub.

restore boot loaders Ubuntu Win xp Vista
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by presence1960 on 2009-10-25
> **oldfred said:**
> atirox, you should start your own thread so that people using search engines can find the right question and answers.

Vista and later seem to be the only systems that allow you to edit the partitions while running. Gparted needs to be loaded from the live cd so no partitions are mounted. If you have xp you should have not problems using gparted. Of course always backup important data just in case. Gparted will not reinstall grub.

Restore boot loaders ubuntu win xp vista
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

+1 
But if you shrink the XP partition using gparted from the Ubuntu Live CD and then resize Ubuntu's partition to add the space you took from XP you should not have to mess with GRUB or windows bootloader.

---

### Post by presence1960 on 2009-10-25
> **atirox said:**
> Okay, so i have the same problem, but with a 40 GB HDD. Its in a Compaq Presario R3055CA. 

Anyway, I already have a partition manager in windows. However, the partition manager tells me that it cant alter the size of the disk, because it is used to boot the system. **It tells me that i'd need to reconfigure GRUB after i resize the partition.** My question is, Does GParted reconfigure Grub, or do I have to do that myself? If I have to do it myself, which is easier, using the partition manager i have in windows, or using GParted? 

Just as a little history behind why I ask, I love this laptop. Its 6 years old. One thing i love best about it is the Broadcom wireless card. It works wonders under windows. If most of you recall, Broadcom doesnt have any open source drivers, especially for the BCM43xx series, which was popular around the time that this machine was made. so i spent a good 3 hours trying to get the stupid thing to work, and I finally got it working. I'd rather not loose all the work i did trying to get the wireless card to work, which is why I don't want to just wipe the partition and reinstall it.

Windows will tell you nothing about GRUB.

If you do what I said in my previous post you should not have to configure GRUB. But in any case if something goes wrong and you need to do post back.

---

### Post by atirox on 2009-10-25
Okay, i'll remember that for next time.

> **presence1960 said:**
> Windows will tell you nothing about GRUB.

Yes, Windows doesnt say anything about GRUB. I messed up there. But Acronis Disk Director Suite does. Here is the warning message I recieved when trying to resize the partition.

> You are about to change the paramaters of the **ext3** partition.

If this is not a bootable partition, click **OK** to continue.

If this is a bootable partition, you will need to perform some actions to make it bootable after the partitioning operations. Please be sure you have your Linux boot diskette before clicking the **OK** button.

In order to make this partition bootable again after partitioning operations are complete, you should:

-Insert the Linux boot diskette into the floppy drive;
-Boot your computer from the Linux boot diskette and login as **root**;
-If you use ASPLoader as the Linux loader, type  **/sbin/aspldr**
-If you use LILO as the Linux loader, type  **/sbin/lilo**
-If you use a different Linux loader, please follow the instructions as described in the software manual for your loader.
-Reboot your computer and you will be able to boot to your Linux again.

I did make the changes in GParted, however, i also resized the swap partition too... im thinking that was a mistake, because the graphics are messed up now... it shows part of the desktop, and the rest is black. Or perhaps i didn't give it enough time to load, since it seems to do that just before the login screen for a split second... we'll see what happens tonight.

Also, as a closing note, thank you guys for the help. Its nice to have. Any recommendations of things i can to to become an Ubuntu expert?

---

