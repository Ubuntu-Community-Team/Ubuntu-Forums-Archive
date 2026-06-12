---
title: "Separate MBR"
date: 2009-10-01
forum: Installation &amp; Upgrades
---

### Post by Dancefloor Innovators on 2009-10-01
This is my current set up:

sda
sda1 - NTFS - Windows 7
sda2 - NTFS - Storage (no operating system)

sdb (MBR)
sdb1 - NTFS - Windows Vista

sdc (I should note that none of this here is commited yet)
sdc1 - Swap
sdc2 - /boot
sdc3 - /
sdc4 - /home

Basically what I'm wanting to do is install GRUB to sdc2, but then have the MBR on sdb point to sdc2. How would I go about doing this? I'm installing 9.02.

Help really appreciated...

---

### Post by binary00mind on 2009-10-01
You can install grub in whatever MBR you want. If you do it on your third hard drive, you will have to bring up the BIOS menu each time you want to boot into Linux. 
Also your layout is wrong. Your plan is to have 4 primary partitions. 
What about the LVM partition? you cannot install LVM as a 5th primary nor extended/logical partition. 
If I were you that is what I would do.
/sdc1 /  as primary
/sdc5 swap as a extended/logical an so on....
/sdc6 /home
/sdc7 LVM 
/sdc8 /var
That is what I would do. But it is your computer so you decide how the final layout will look. 
Also more info would be nice..is the dev/sdb & /dev/sdc internal or external...I would guess that the third HD /sdc is an a portable HD?

---

### Post by Dancefloor Innovators on 2009-10-01
> **binary00mind said:**
> You can install grub in whatever MBR you want. If you do it on your third hard drive, you will have to bring up the BIOS menu each time you want to boot into Linux. 
Also your layout is wrong. Your plan is to have 4 primary partitions. 
What about the LVM partition? you cannot install LVM as a 5th primary nor extended/logical partition. 
If I were you that is what I would do.
/sdc1 /  as primary
/sdc5 swap as a extended/logical an so on....
/sdc6 /home
/sdc7 LVM 
/sdc8 /var
That is what I would do. But it is your computer so you decide how the final layout will look. 
Also more info would be nice..is the dev/sdb & /dev/sdc internal or external...I would guess that the third HD /sdc is an a portable HD?
sda has windows on it. sdb also has windows on it and is the location of the mbr. sdc will have ubuntu on it. All three drives are internal.

There is also no LVM option available in the partition editor.

---

### Post by binary00mind on 2009-10-02
I'm thinking that you are using a Windows or DOS partition editor where you won't find any LVM let alone the code for it... 
BTW how you planning to install your Ubuntu? from live CD or alternate text installer CD? 
Either way do yourself a favor and leave the partitioning to the installer. You can manually set the size of each partition and what kind of mount points you are preferring. 
If You do the partitioning by yourself, the installer will format your self-created partitions anyway.
LVM stands for Logical Volume Manager and the smallest size is I believe 49.3 MB but under Windows you just make a raw partition you can make any size but it must be at least 50MB.  
If I were You, I would use alternate text installer CD...it is easy and much better installation then from the live CD. Just follow the steps
it is a breeze. 
As far as the grub goes. Install the grub in the main MBR /dev/sda 
and You can boot into any OS you want from there. 
But make sure that the installer recognize all your existing Windows OS's. It will happen right before installation of the grub.

---

### Post by oldfred on 2009-10-02
I am not quite sure why binary00mind wants a LVM. I do not use one and boot 3 hard drives. I thought LVM was to span volumes or for very large drives.

You can install grub to any MBR but the only one that counts is whatever BIOS thinks is first, and that is not always the same as what grub and linux think is first.

Did your Win7 and Vista combine their boot into one. If so you will not be able to directly boot in Grub as windows has moved boot files. Possible solution:
Vista copies boot manager to one 
[http://members.iinet.net/~herman546/p15.html#BOOTMGR_is_missing](http://members.iinet.net/~herman546/p15.html#BOOTMGR_is_missing)
Moral of the story - look on other NTFS partitions for the missing bootmgr and Boot directory.

I like to have something in the MBR of every bootable disk just incase the boot drive fails, I can reboot, change boot order in BIOS and get into my system without a live CD.

---

### Post by binary00mind on 2009-10-02
I must agree with you on most points. As I myself with Win7 plus 7 Linux OS's on total of 11 HD's. 
I can boot into any OS from any MBR HD where the grub's are installed. Like you, I like to have the escape route, just in case. 
The reason I like to have LVM and the logical drives is, that in the future one has the room to play around with the partitions. 
Committing yourself to 4 primary partitions, leave one with very little room or no room to change things if there is a need to create new partition or resize. 
Another thing is that in the case of corrupted PT, it is easier to recover logical HD versus primary ones, since the extended/logical drives leave PT data trail one after the other
Also with Dancefloor Innovators HD layout, there is no /var partition, which for me is very important.

---

### Post by Zimmer on 2009-10-02
Have you thought of installing EasyBCD to the Vista drive ?

[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

This might be of interest,too

[http://www.multibooters.co.uk/](http://www.multibooters.co.uk/)

---

