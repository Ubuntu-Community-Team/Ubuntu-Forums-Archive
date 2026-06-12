---
title: "RAN out of disk space in filesystem..!!! ?"
date: 2009-08-11
forum: Installation &amp; Upgrades
---

### Post by madhavhmk on 2009-08-11
Hi,

I had given a partition of just 7 GB for linux...I had begun using it on a trial basis, but I am liking it very much..!!!!

My HDD has 160 GB space and I can free some space from windows and make it as ext3 extension...

is there anyway I can add the free space to existing filesystem without formatting?

Or is there a way in which I can direct ubuntu to use the free space also as part of filesystem...?

Please help me out...

thanks

---

### Post by merlinus on 2009-08-11
This may help:

[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)

---

### Post by tommcd on 2009-08-11
Do you only have 1 partition for Ubuntu? Or do you have separate root and home partitions? Post the output of:
```
sudo fdisk -l
```
Anyway, you can use a Parted Magic live CD to shrink your Windows partition and create some free space. Then you can expand the Ubuntu partition to use that newly allocated free space. Get Parted Magic here:
[http://partedmagic.com/](http://partedmagic.com/)

---

### Post by madhavhmk on 2009-08-11
This is my output for fdisk..

I have several partitions for windows....but only one for linux


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc8000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *       19131       19458     2620416    c  W95 FAT32 (LBA)
/dev/sda2              10        1315    10485760    7  HPFS/NTFS
/dev/sda3   *        1315        9147    62914560    7  HPFS/NTFS
/dev/sda4            9148       19458    82815716    f  W95 Ext'd (LBA)
/dev/sda5            9756       19130    75302912    7  HPFS/NTFS
/dev/sda6           19131       19458     2620416   dd  Unknown
/dev/sda7            9148        9755     4883728+  83  Linux

---

### Post by madhavhmk on 2009-08-11
Thankyou Merlinus, for the link....

and I needed to know if it would be possible to add space to an existing partition with partition magic....

then using this software, it would be pretty straightforward, I think....
Thanks tommcd..!!

---

### Post by tommcd on 2009-08-11
> **madhavhmk said:**
> This is my output for fdisk..

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc8000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *       19131       19458     2620416    c  W95 FAT32 (LBA)
/dev/sda2              10        1315    10485760    7  HPFS/NTFS
/dev/sda3   *        1315        9147    62914560    7  HPFS/NTFS
/dev/sda4            9148       19458    82815716    f  W95 Ext'd (LBA)
/dev/sda5            9756       19130    75302912    7  HPFS/NTFS
**/dev/sda6           19131       19458     2620416   dd ** Unknown
/dev/sda7            9148        9755     4883728+  83  Linux
What is /dev/sda6 that fdisk says it is "unknown"? You could delete that using Parted Magic (or GParted) if you don't need it; and then grow your Ubuntu partition into that. You should also be able to shrink the NTFS partition on /dev/sda5 if you need more space.
If you did delete /dev/sda6, then your Ubuntu partition would then become /dev/sda6. This should not pose a problem with grub when booting Ubuntu, since grub boots Ubuntu by it's UUID instead of the partition number. The UUIDs do not change when you move partitions around like this.

---

### Post by merlinus on 2009-08-11
According to fdisk, sda1 and sda6 occupy the same hdd space.  Also, the partitions are not in correct numerical order.

It might be worthwhile to try and fix it from a terminal or CLI:

```
sudo fdisk /dev/sda
x
f
w
```

---

### Post by madhavhmk on 2009-08-11
I remember, at the time of installing linux, there was a provision for swap partition or swap space.....it was also mentioned that I can change the size of this space after I have installed linux....

I think that "unknown" mentioned as sda6 is actually a swap space of some kind...anyway I ll check it out....


Thanks...!!!!

---

### Post by madhavhmk on 2009-08-11
In windows there is a 

C: drive approx 60 GB
G: with approx 70 GB
MEdia direct 
recovery
 
and Linux with 8GB

------------
Now that I have noticed it, the sda1 and sda6 seems to be the media direct...

in linux, I can see two links for "media direct" in the places menu..although they point to same partition..

---

### Post by madhavhmk on 2009-08-11
Now my grub seems to be corrupted..!!!!!!

I am not able to view the list of operating systems now...!!!after running the commands of merlinus....

now an error 17 is being displayed at startup

---

### Post by merlinus on 2009-08-11
To fix grub, boot from live cd, open a terminal and enter these commands one at a time:

```
sudo grub
find /boot/grub/stage1 #you will get a response such as root (hd0,2)
root (hd0,2) #use hd and numbers from the previous command
setup (hd0)  #use hd and its number from the previous command
quit 
```Remove the cd and restart.

If this does not work, try supergrub:

[http://supergrubdisk.org](http://supergrubdisk.org)

---

### Post by madhavhmk on 2009-08-11
the find was not locating the file you specified....some error 15 was coming up saying no data file...

But I mounted the sda5(linux) which seemed to be the new mount point for linux and edited the /boot/grub/menu.lst file

and set up grub to (hdd0, 4)

I also had to edit the settings for windows...but I finally got it working..!!


Thanks..but your command for arranging the HDDS worked fine...

---

