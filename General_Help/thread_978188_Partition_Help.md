---
title: "Partition Help"
date: 2008-11-10
forum: General Help
---

### Post by unbuntunoob321 on 2008-11-10
hey guys i wondering if you guys can help me out on partitoning my hard drive during the ubuntu installation.

i tried to pick the "guided resize" but i get this error message:
[http://i165.photobucket.com/albums/u74/robrobs/Screenshot.png](http://i165.photobucket.com/albums/u74/robrobs/Screenshot.png)

so i guess i have to manually partition my hard disk... 

how do i partition it if i want to dual boot with windows XP?

this is what comes up at the manual partition screen:
[http://i165.photobucket.com/albums/u74/robrobs/Screenshot-3.png](http://i165.photobucket.com/albums/u74/robrobs/Screenshot-3.png)

---

### Post by TeXtonyx on 2008-11-11
Resize your XP partition before starting the Ubuntu install process.
Test to make sure XP still boots. Then, during the install, choose
'largest free space (guided). This will avoid overwriting your XP
installation. Or if you want to manually create your partitions
read a howto guide; in any event it is safer to resize your 
partitions before you install Ubuntu. Once in awhile installing
Ubuntu by resizing the partition corrupts the XP boot sector. 

Another option besides installing grub to the MBR is to install it
to the /boot partition. Then you need to use Bootpart to add Ubuntu
to boot.ini and you will boot from the XP bootloader. Another way
is, [http://ubuntuforums.org/showthread.php?t=899222](http://ubuntuforums.org/showthread.php?t=899222) is a pictorial 
guide and recommends an alternate bootloader.

"You will now be presented with the partitioning options. Ubuntu 
"intelligently" offers to resize your windows partition and do 
everything automatically. I advise AGAINST using this option, 
and instead select the manual option and click forward ..."

TeX: I advise resizing the partition beforehand.

---

### Post by unbuntunoob321 on 2008-11-11
gah this is really frustrating >.< 

i went to partition on windows xp and the link was broken
and by broken i mean when i double click it, nothing happens.

---

### Post by bodhi.zazen on 2008-11-11
Start by booting windows XP, back up your data (resizing is normally safe, but you never know), check how much free space you have, and most important defragment windows XP.

Then boot the Ubuntu Desktop CD and use gparted to resize windows.

It is quite easy :)

[Gparted Documentation](http://gparted.sourceforge.net/documentation.php)

---

### Post by uidb4056 on 2008-11-11
But be aware that as showed in your second screen-shot you have 4 partitions currently in your disk, if all of them are primary you will not be able to create new partition (4 primary is the maximum allowed), if it is then you need to delete at least one partition resize the remaining and create an extended partition to hold logical partitions for root (/) and swap.

---

### Post by unbuntunoob321 on 2008-11-11
> **uidb4056 said:**
> But be aware that as showed in your second screen-shot you have 4 partitions currently in your disk, if all of them are primary you will not be able to create new partition (4 primary is the maximum allowed), if it is then you need to delete at least one partition resize the remaining and create an extended partition to hold logical partitions for root (/) and swap.

ok, but what are sda1, sda5, and sda4?
(im assuming sda2 is windows xp?)
and how do i get rid of them?

while keeping XP

---

### Post by bodhi.zazen on 2008-11-12
This thread should help a little :

[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

---

