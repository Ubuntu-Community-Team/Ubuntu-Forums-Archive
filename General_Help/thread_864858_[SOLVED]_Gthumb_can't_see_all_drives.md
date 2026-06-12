---
title: "[SOLVED] Gthumb can't see all drives"
date: 2008-07-20
forum: General Help
---

### Post by Spaceman9 on 2008-07-20
Nautilus can see my 3 hard drives. Gthumb can only see the drive I have Ubuntu installed on which is my boot drive. It can't see my second and third drives. How do I fix this? 

In Gthumb in media it shows 2 cdrom's, but I only have 1. It shows 1 disk, but when I click on disk it doesn't show anything on the disk. And it shows 3 floppy drives. I only have 2 floppy drives. If I go back to home it shows the folders in home on the drive I have Ubuntu installed on.

Thankx for any help.

---

### Post by Spaceman9 on 2008-07-20
bump

---

### Post by Spaceman9 on 2008-07-20
bump

---

### Post by bapoumba on 2008-07-20
Are your other hard drives ext3 ?

---

### Post by Spaceman9 on 2008-07-20
Yes. First drive Ubuntu, second drive PCLOS, third drive for backing up data files. All 3 formated with ext3.

---

### Post by Spaceman9 on 2008-07-21
bump

---

### Post by Spaceman9 on 2008-07-21
bump

---

### Post by bapoumba on 2008-07-21
Well, I have no real idea, sorry, as I can see other partitions and other removable drives with gThumb. I have only one hard drive, so I cannot trouble check, and did not find anything related on the internets.

---

### Post by Spaceman9 on 2008-07-21
Ok, thankx for your help. May be some one else knows.

---

### Post by Spaceman9 on 2008-07-22
bump

---

### Post by Spaceman9 on 2008-07-22
bump

---

### Post by Spaceman9 on 2008-07-22
I discovered if I open Nautilus and click on the drive I want to look at with gthumb then gthumb can see that drive, but shouldn't gthumb see the other drives on my computer without having to click on the drive with Nautilus. This problem is sending me round the bend.

---

### Post by bapoumba on 2008-07-23
> **Spaceman9 said:**
> I discovered if I open Nautilus and click on the drive I want to look at with gthumb then gthumb can see that drive, but shouldn't gthumb see the other drives on my computer without having to click on the drive with Nautilus. This problem is sending me round the bend.
May be you should open a bug report on Launchpad.

---

### Post by Spaceman9 on 2008-07-23
Merci. I'll file a bug report. I'm not sure it's a bug though. I used Debian last year for 3 months and I had problems with hard drives in that distro too. May be my computer just doesn't like Debian stuff. I don't know.

---

### Post by bapoumba on 2008-07-23
De rien :)
I just found this one: [lpbug]37777[/lpbug]

---

### Post by Spaceman9 on 2008-07-23
Thank you for the link. I just read it. Also I sent a bug report. One really strange thing though. I installed KDE last week and when I'm in Gnome and I use ShowPhoto that program sees all of my hard drives. ShowPhoto is really a KDE app I think. 

So, I guess it's just the way gthumb works. I don't know. I could say I haven't had this problem in other distros, but I do love Ubuntu. It just drives me nuts sometimes.

---

### Post by danwood76 on 2008-07-23
Where abouts are your drives mounted to?

It could be that it only looks in /media (though obviously if theyre mounted there just ignore me ;))

---

### Post by Spaceman9 on 2008-07-23
Oi danwood76, jolly nice of you to drop by old bean. I'm not sure I understand what you mean when you ask “Where abouts are your drives mounted to?” Do you mean fstab?

This is my bug report.
Binary package hint: gthumb
1. Ubuntu 8.04 LTS
2. Package gthumb 3:2.10.8-0ubuntu1
3. I thought gthumb would see all 3 of my internal pata hard drives.
4. It doesn't. In media it shows 2 cdrom drives, but I only have 1 cdrom drive. It shows 3 floppy drives, but I only have 2 floppy drives. It shows disk which is a usb pen drive. It shows disk-1, but when I click on that it doesn't show anything in that disk. It doesn't show my other 2 hard drives at all. In mnt it shows nothing.
I can access my other 2 hard drives with Nautilus but not with gthumb.

This is my menu.lst
default		9

timeout 30

color black/light-gray black/blue



#A splash image for the menu

splashimage=(hd0,0)/boot/grub/splashimages/debian-moreblue-swirl.xpm.gz



title Ubuntu 8.04, kernel 2.6.24-18-generic

root (hd0,0)

kernel /boot/vmlinuz-2.6.24-18-generic root=UUID=00186574-55f8-44d1-ac03-04b9ebb7cc9a ro quiet splash

initrd /boot/initrd.img-2.6.24-18-generic

quiet



title Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)

root (hd0,0)

kernel /boot/vmlinuz-2.6.24-18-generic root=UUID=00186574-55f8-44d1-ac03-04b9ebb7cc9a ro single

initrd /boot/initrd.img-2.6.24-18-generic



title Ubuntu 8.04, kernel 2.6.24-16-generic

root (hd0,0)

kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=00186574-55f8-44d1-ac03-04b9ebb7cc9a ro quiet splash

initrd /boot/initrd.img-2.6.24-16-generic

quiet



title Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)

root (hd0,0)

kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=00186574-55f8-44d1-ac03-04b9ebb7cc9a ro single

initrd /boot/initrd.img-2.6.24-16-generic



title Ubuntu 8.04, memtest86+

root (hd0,0)

kernel /boot/memtest86+.bin

quiet



title Other operating systems:

root 



title linux (on /dev/sdb1)

root (hd1,0)

kernel /boot/vmlinuz BOOT_IMAGE=linux root=/dev/hdb1 acpi=on resume=/dev/hdb5 splash=silent vga=788

initrd (hd1,0)/boot/initrd.img

savedefault



title linux-nonfb (on /dev/sdb1)

root (hd1,0)

kernel /boot/vmlinuz BOOT_IMAGE=linux-nonfb root=/dev/hdb1 acpi=on resume=/dev/hdb5

initrd (hd1,0)/boot/initrd.img

savedefault



title failsafe (on /dev/sdb1)

root (hd1,0)

kernel /boot/vmlinuz BOOT_IMAGE=failsafe root=/dev/hdb1 failsafe acpi=on resume=/dev/hdb5

initrd (hd1,0)/boot/initrd.img

savedefault

### BEGIN AUTOMAGIC KERNELS LIST


This is my fstab
# /etc/fstab: static file system information.

#

# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc            /proc           proc    defaults        0       0

# /dev/sda1

UUID=00186574-55f8-44d1-ac03-04b9ebb7cc9a /               ext3    relatime,errors=remount-ro 0       1

# /dev/sda5

UUID=cb772597-a441-4caf-a123-8c8fe300956c /home           ext3    relatime        0       2

# /dev/sda6

UUID=4db8a804-f90a-4ac6-a93d-51ed119ee827 none            swap    sw              0       0

# /dev/sdb5

UUID=8070c047-730f-4378-ae5a-869eb51318f6 none            swap    sw              0       0

# /dev/sdc5

UUID=4766e575-f47c-454d-8d8e-7bae96ff910b none            swap    sw              0       0

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

/dev/fd0        /media/floppy0  auto    rw,users,noauto,fmask=111,dmask=000,exec,utf8 0       0

/dev/sdd        /media/floppy1  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by danwood76 on 2008-07-23
Hi there.

Your 2 extra internal disks arent in your fstab?
How are they mounted when you access the data on them?

It could be that gthumb doesnt use GVFS so although you can see them in nautilus gthumb cant see them.

I have just proven this by mounting a network drive through gvfs and sure enough gthumb cant see it.
If you were to mount your drives to /media/DRIVE they will proibably show up in gthumb.

---

### Post by Spaceman9 on 2008-07-23
> **danwood76 said:**
> Hi there.

Your 2 extra internal disks arent in your fstab?
How are they mounted when you access the data on them?

It could be that gthumb doesnt use GVFS so although you can see them in nautilus gthumb cant see them.

I have just proven this by mounting a network drive through gvfs and sure enough gthumb cant see it.
If you were to mount your drives to /media/DRIVE they will proibably show up in gthumb.


My Kingdom for a GVFS! I haven't the foggiest what a GVFS is. Can I buy one at WalMart?

Aren't the 2 drives listed below my other 2 drives? 
# /dev/sdb5

UUID=8070c047-730f-4378-ae5a-869eb51318f6 none swap sw 0 0

# /dev/sdc5

UUID=4766e575-f47c-454d-8d8e-7bae96ff910b none swap sw 0 0


How do I mount my drives to /media/DRIVE??

---

### Post by danwood76 on 2008-07-23
Theyre listed as swap partitions and so will be mounted in such a way.

If they arent swap and you want to mount them you need to specify a mount point and filesystem type.

Do:
```

sudo fdisk -l
sudo blkid

```
And I will be able to tell you, and also give you a couple more fstab lines if you want them to mount at bootup.

-- edit --

Sorry GVFS (Gnome Virtual File System) is a new way to access mounted devices in GNOME.
It replaces the old system and has only been introduced in the latest GNOME release.
Some apps havent been updated to use GVFS and so they dont see all the mounted drives that all other GNOME apps can.

---

### Post by Spaceman9 on 2008-07-23
So this kurfuffle is all down to gnome changing it's file system! That really curdles my clotted cream.

I thought swap was never to be mounted. I wouldn't want to mount swap. I have my reputation to think of you know...lol


bruce@bruce-desktop:~$ sudo fdisk -l
[sudo] password for bruce: 

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9d279d27

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         937     7526421   83  Linux
/dev/sda2             938        4865    31551660    5  Extended
/dev/sda5             938        4791    30957223+  83  Linux
/dev/sda6            4792        4865      594373+  82  Linux swap / Solaris

Disk /dev/sdb: 40.9 GB, 40971829248 bytes
255 heads, 63 sectors/track, 4981 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x90909090

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1019     8185086   83  Linux
/dev/sdb2            1020        4981    31824765    5  Extended
/dev/sdb5            1020        1528     4088511   82  Linux swap / Solaris
/dev/sdb6            1529        4981    27736191   83  Linux

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00063242

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       14469   116222211   83  Linux
/dev/sdc2           14470       14593      996030    5  Extended
/dev/sdc5           14470       14593      995998+  82  Linux swap / Solaris

Disk /dev/sdd: 8387 MB, 8387559424 bytes
64 heads, 32 sectors/track, 7999 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Disk identifier: 0xe8b143b8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1        7999     8190960   83  Linux
bruce@bruce-desktop:~$ sudo blkid
/dev/sda1: UUID="00186574-55f8-44d1-ac03-04b9ebb7cc9a" TYPE="ext3" SEC_TYPE="ext2" 
/dev/sda5: UUID="cb772597-a441-4caf-a123-8c8fe300956c" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb1: UUID="cae56b85-9719-4340-a8f8-e3cb5e0950c5" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: TYPE="swap" UUID="8070c047-730f-4378-ae5a-869eb51318f6" 
/dev/sdb6: UUID="dd500520-cbb9-4481-9670-81cd69c692b3" TYPE="ext2" 
/dev/sdc1: UUID="4a4062e0-e07d-4012-b7b2-80eb19f8125b" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc5: TYPE="swap" UUID="4766e575-f47c-454d-8d8e-7bae96ff910b" 
/dev/sda6: TYPE="swap" UUID="4db8a804-f90a-4ac6-a93d-51ed119ee827" 
/dev/sdd1: UUID="a505be70-8ed5-499d-acfc-c66402913213" TYPE="ext3" 
bruce@bruce-desktop:~$

---

### Post by danwood76 on 2008-07-23
> **Spaceman9 said:**
> 
I thought swap was never to be mounted. I wouldn't want to mount swap. I have my reputation to think of you know...lol


Hehe, I'm sure you do.

The new GVFS is far better than GnomeVFS (its predecessor) its just very young so you have to take it with a pinch of salt.

From the output of those commands I can see you are indeed mounting the swap up.
(Swap is mounted but not in the usual sense of mounting as the user has no access to it but the kernel uses it)

Ok so I assume you want the three linux partitons on sdb and sdc.

We can see that these are:
```

/dev/sdb1 * 1 1019 8185086 83 Linux
/dev/sdb1: UUID="[COLOR="Red"]cae56b85-9719-4340-a8f8-e3cb5e0950c5[/COLOR]" SEC_TYPE="ext2" TYPE="[COLOR="Red"]ext3[/COLOR]"

/dev/sdb6 1529 4981 27736191 83 Linux
/dev/sdb6: UUID="[COLOR="Red"]dd500520-cbb9-4481-9670-81cd69c692b3[/COLOR]" TYPE="[COLOR="Red"]ext2[/COLOR]"

/dev/sdc1 * 1 14469 116222211 83 Linux
/dev/sdc1: UUID="[COLOR="Red"]4a4062e0-e07d-4012-b7b2-80eb19f8125b[/COLOR]" SEC_TYPE="ext2" TYPE="[COLOR="Red"]ext3[/COLOR]"

```

So the lines that need to be added to the fstab are:
```

UUID=cae56b85-9719-4340-a8f8-e3cb5e0950c5 /media/sdb1 ext3 relatime 0 2
UUID=dd500520-cbb9-4481-9670-81cd69c692b3 /media/sdb6 ext2 relatime 0 2
UUID=4a4062e0-e07d-4012-b7b2-80eb19f8125b /media/sdc1 ext3 relatime 0 2

```
(I would delete the two entries pointing to the two swaps as you only need one active.)

You will then have to create these mount points:
```

sudo mkdir /media/sdb1
sudo mkdir /media/sdb6
sudo mkdir /media/sdc1

```
I would probably give it a restart as you want to make sure theyre all unmounted before you mount them.

You should then have sdb1 sdb6 and sdc1 on your desktop and with a bit of luck they will also appear in gthumb.

---

### Post by Spaceman9 on 2008-07-23
Why do I only need one swap active? I thought the more swap space I have the better. And shouldn't I have a swap on each drive?

---

### Post by danwood76 on 2008-07-23
The kernel only really uses swap when you have no RAM left, its like a virtual memory cache but its obviously a lot slower than RAM.
Its also used when you hibernate.

Generally you only need at least 1GB swap or equal to the amount of RAM if larger than that and you only need it in one place.
If you have multiple linux distros they can all share swap space as long as you dont hibernate any of them to it.

I have several disks in my desktop system and only one swap which with 2GB of RAM sees about 4KB of usage ever and only really when I'm doing a lot of video conversion/editing.

---

### Post by Spaceman9 on 2008-07-23
Right, but and however as well an all, I do computer graphics (digital painting and such) and some of my paintings in memory are 1.5GB or more. I only have 256MB of RAM...although I have many more sheep...never mind. So wouldn't I need a lot of swap?

---

### Post by danwood76 on 2008-07-23
> **Spaceman9 said:**
> I only have 256MB of RAM

Oh my god how do you live with such a small amount? :)

You can use swap to add more virtual RAM but it will slow your machine down heavily in the process.
The better option is to spend the £20 and get a GB of RAM, you will notice the speed increase believe me.

In answer to your question though, with such a small amount of RAM it might be worth you using 3 swap partitions on seperate drives.
It has the advantage of faster disk access compared to a single swap.
So keep them. :)

---

### Post by Spaceman9 on 2008-07-23
Jolly good. Three it is then.

Right, I'll carry on with adding the lines to my fstab. I'll have to do that later though. I'm going down the shops now. Cheers and ta very much for all the help mate.

---

### Post by Spaceman9 on 2008-07-23
I set up everything in fstab and gthumb can see the drives now. Well done you!

---

