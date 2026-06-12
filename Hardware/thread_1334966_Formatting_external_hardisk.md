---
title: "Formatting external hardisk"
date: 2009-11-23
forum: Hardware
---

### Post by eshi14 on 2009-11-23
hi 
i have a 250 gb hard disk. I have about 160 gb filled, now i want to create a primary partition, to install another operating system. So is there a way so i can create a partition without removing the existing data.
i was using Gpart but without any success.

HELP PLEASE...:roll:

---

### Post by prshah on 2009-11-23
> **eshi14 said:**
> i want to create a primary partition, to install another operating system.

i was using Gpart but without any success.


We need to know about your current partition setup to offer competent advice. Please open a terminal (Applications-Accessories-Terminal) and post back the output of the following command```
sudo fdisk -l
``` Or you can post back a screenshot of the gparted window.

Gparted should be able to do as you ask. What is the exact error/problem you are facing with gparted?

You can have only a maximum of 4 primary partitions. If you already have 4, you cannot add any more. The workaround for this is to usually designate 1 of the 4 primary partitions as an "extended" partition, which can then house multiple "virtual" partitions within it.

If your partition currently occupies the entire disk, then you will need to "shrink" it before you can add a new partition. Gparted can do this for you, but there is a small chance of data loss so please ensure you backup before you attempt this. After you shrink your existing partition you can then create a new partition subject to the conditions above.

Please post back the output to the fdisk command for more relevant and exact advice.

---

### Post by eshi14 on 2009-11-23
> Please post back the output to the fdisk command for more relevant and exact advice.hi prshah,

this is the screen shot and i don't have any primary partition on the drive. The problem is i have about half of my drive filled so its difficult to make a back up ...So is tere a possible way to make a partition without a backup...
Moreover this partition is not getting detected in windows .. It says I need to format the drive again...
what do i do ...!!!

Thanx for replying

Surabhi.

---

### Post by prshah on 2009-11-23
> **eshi14 said:**
> i don't have any primary partition on the drive. 

I think you are a little confused; let me try to clear things up.

In the second screenshot, I don't think your external drive was connected; which makes the screenshot irrelevant.

In the first screenshot, we see that you have a single primary partition spanning the entire disk. All partitions number from 1-4 (/dev/sdb[color=red]1[/color]) are primary partitions; those numbered from 5 onwards are logical partitions/drives.

If your current partition is not opening in Windows, it indicates some other problem. Please check this before you do any partition shrinking.

Now in your case, the external HDD has a single partition spanning the entire drive. This partition needs to be "shrunk" to make some "unpartitioned" space available. This unpartitioned space can then be used to make a second primary partition.

The steps from ubuntu:

a) plug in your external hdd
b) If it mounts, please unmount it. (Right click the desktop icon, choose "Unmount" or "safely remove")
c) Open gparted, and select your external HDD
d) Make sure there is no "keys" icon next to the partition line. If there are any keys icon then it means that the partition is not unmounted. Please unmount it and restart gparted.
e) Right click the partition and choose "Resize/Move". Reduce the size as you feel suitable.
f) Click apply. gparted will now reduce the size of the partition and leave the rest as "unpartitioned" space. This can take a considerable amount of time, and should not be interrupted.
g) You can now proceed to install your other OS, and choose to use the unpartitioned space. 

I advise you to take a backup; it may not prove necessary. I understand your space constraints, but in that case you and you only can decide whether you should take the risk or not.

Gparted is not to be used lightly and carelessly, please be alert and careful.

Please post back if you have further questions.

---

