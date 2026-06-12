---
title: "Dual boot/drive data partitions"
date: 2009-09-07
forum: Installation &amp; Upgrades
---

### Post by jrysatx on 2009-09-07
I intend to make my system a dual boot with XP and Ubuntu to try out Ubuntu. I have a dual drive system one for opsys and one for data. Can I partition drive two with /home to keep my data separate? I keep my windows data on this drive as well. Any ideas/suggestions?

---

### Post by running_rabbit07 on 2009-09-07
> **jrysatx said:**
> I intend to make my system a dual boot with XP and Ubuntu to try out Ubuntu. I have a dual drive system one for opsys and one for data. Can I partition drive two with /home to keep my data separate? I keep my windows data on this drive as well. Any ideas/suggestions?

Yes you can install that way but you will have to make sure that the Grub boot loader is installed in the Master Boot Record.

---

### Post by kennethadammiller on 2009-09-08
What i'm getting is this-that you have one drive for data, one for operating systems. Well i don't know that you can configure linux to use an external media as it's home environment, but yes you can use an external drive as the media bay for both linux and windows, just make sure that when windows is turned off, the drive is unmounted. this way linux will be able to mount it.
what I suggest is using hard drive one to install both operating systems and then just picking a specific hard drive format for the one to hold the data. Linux doesn't have propriety codes for NTFS so.... it can still write to it i know. it works fine when linux uses it but if you try to write to the partition that your windows is on with linux it can mess things up. i think...
if you like you can let one part of the other hard drive be ext3 or ext4 for linux only. 

... i don't know if you can get windows to use ext types... you might look around.

---

### Post by jrysatx on 2009-09-08
> **running_rabbit07 said:**
> Yes you can install that way but you will have to make sure that the Grub boot loader is installed in the Master Boot Record.
 
Is there any documentation to do what I am trying to do? Where do I get the Grub boot loader? Is Gnu Grub a newer version of it? Thanks for the quick answer.

---

### Post by jrysatx on 2009-09-08
> **kennethadammiller said:**
> What i'm getting is this-that you have one drive for data, one for operating systems. Well i don't know that you can configure linux to use an external media as it's home environment, but yes you can use an external drive as the media bay for both linux and windows, just make sure that when windows is turned off, the drive is unmounted. this way linux will be able to mount it.
what I suggest is using hard drive one to install both operating systems and then just picking a specific hard drive format for the one to hold the data. Linux doesn't have propriety codes for NTFS so.... it can still write to it i know. it works fine when linux uses it but if you try to write to the partition that your windows is on with linux it can mess things up. i think...
if you like you can let one part of the other hard drive be ext3 or ext4 for linux only. 
 
... i don't know if you can get windows to use ext types... you might look around.
 Thanks for the answer.... what I am trying to do is put Ubuntu and windows on a dual boot drive, (C:), and data for windows, and /home for Ubuntu on (D:). I want to use both operating systems until I can determine that Ubuntu will do all I want it to, then boot windows for good. I understand I have to understand Grub on the MBR to make the system dual boot, just not sure if each opsys can find the data for each. I can partition the data drive for windows and /home.... I think, hope. That's where I am going. Where can I get Grub, and if there is any documentation to do what I am trying to do?

---

### Post by presence1960 on 2009-09-08
> **jrysatx said:**
> Thanks for the answer.... what I am trying to do is put Ubuntu and windows on a dual boot drive, (C:), and data for windows, and /home for Ubuntu on (D:). I want to use both operating systems until I can determine that Ubuntu will do all I want it to, then boot windows for good. I understand I have to understand Grub on the MBR to make the system dual boot, just not sure if each opsys can find the data for each. I can partition the data drive for windows and /home.... I think, hope. That's where I am going. Where can I get Grub, and if there is any documentation to do what I am trying to do?

GRUB will be installed during the Ubuntu install process. it will be installed on the MBR of your boot hard disk by default. You will have to do nothing.

In order to install a separate home partition create the Ubuntu / (ext3 or ext4), swap (linux-swap) & /home (ext3) partitions before the install. On the prepare disk space window of the ubuntu installer(window 4 of eight) choose Manual (Advanced) option. 

You will then highlight the / partition and click Edit. Set parameters Use as ->choose ext 3 or ext 4, tick the format box, and mount point use the drop down box to select /   ...Save.

Next highlight the swap partition, click Edit & choose use as -> linux-swap. Save

Lastly highlight /home partition & click Edit. Set parameters Use as -> ext3 (I would use ext 3 so any linux can access it. if you use ext 4 you cannot access ext 4 from ext 3). **Tick the format box only if your data is not already on the partition. If data is already on leave the format box unticked.** Set mount point using the drop down box to /home.  Save. Continue with install.

---

