---
title: "[SOLVED] Moving the /home folder"
date: 2008-08-22
forum: General Help
---

### Post by FizzBuntu on 2008-08-22
OK
I need to make room on my system drive and I need to have extra room for my files (in my /home folder)
I thought I could maybe move my file elsewhere (on another drive partition) and make a symbolic link to it...

But it seems that there would be a better (and cleaner) way to do it by mounting a partition as /home

I just couldn't figure it out for sure and from the posts I've read so far, it might go really bad if there is any problem with authorization and ownership ...

so to be clear
1 - Is the symbolic link such a bad idea ?
2 - If the "mounting another partition as /home" is better, how do I do it (without loosing any data of course)

as a side question
3 - Wouldn't it be usefull in the initial Ubuntu installation to seperate the system partition from the data partition (as it is a very common practuce in windows) so that if I need to re-install my Ubuntu I just have to tell him where's my /home and I'm good ?
(that is, of course, if the mounting the /home is possible)

thx

---

### Post by aloshbennett on 2008-08-22
The main advantage of having your home in a different partition is, as you said, when you want to wipe out your OS and start again. I am not sure if that can be done post installation.

When you install ubuntu, you have the option of using a seperate drive as your home.

Considering all is set, symbolic link isnt a bad idea :)

---

### Post by coffeecat on 2008-08-22
But a symbolic link will only work if you've mounted the partition you've put home on, and if you've mounted home to /home, then you won't need a symbolic link.

I've never done this with /home, but I've done it with /boot when I wanted a separate /boot partition, and it worked with /boot, but I can't be 100% sure this will work.

Create another partition for home. Copy all the contents of /home (§) into it - that is /username1, /username2, and so on. Create an entry in /etc/fstab something like:

```
/dev/whichever_partition    /home   ext3   defaults,noatime  0 1
```As I said, I'm not 100% sure about the options and the '0 1' fields, so see if anyone else posts. You should be OK for permissions because /home itself is owned by root. Only /username1, /username2 and so on are owned by username*. Just be careful when you copy over that you retain permissions or you may need to do a bit of chowning and chmodding afterwards.

**§ Edit:** and copy all the contents onto a second medium as a back up, because you need to end up with an empty /home folder on your / partition and if something goes wrong, you'll want to copy all your personal files and folders back into /home again. Don't forget that there are a whole load of hidden configuration files in your home folder as well. Think this one through before proceeding.

---

### Post by FizzBuntu on 2008-08-29
OK, I've tested both solution (symbolic link and mount)
and both works even if symbolic link was easier to put to work, the whole thing was pretty straight forward.

The only thing I still have to figure out is to make nautilus hide the partition mounted as home to only display it in my home 'cause now I'm having my home folder plus ad drive marked as my home folder...

---

### Post by coffeecat on 2008-08-29
> **FizzBuntu said:**
> The only thing I still have to figure out is to make nautilus hide the partition mounted as home to only display it in my home 'cause now I'm having my home folder plus ad drive marked as my home folder...

I'm having difficulty visualising what's going on here. Please post:

1 Output of 'sudo fdisk -l' (That's lower-case L, not one.)

2 Contents of /etc/fstab

3 Some screenshots of Nautilus windows showing exactly what you mean.

---

### Post by FizzBuntu on 2008-09-04
Here's fdisk -l

Disque /dev/sda: 41.1 Go, 41110142976 octets
255 heads, 63 sectors/track, 4998 cylinders
Units = cylindres of 16065 * 512 = 8225280 bytes
Identifiant disque: 0x0007523b

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/sda1   *           1        4787    38451546   83  Linux
/dev/sda2            4788        4998     1694857+   5  Extended
/dev/sda5            4788        4998     1694826   82  Linux swap / Solaris

Disque /dev/sdb: 41.1 Go, 41110142976 octets
255 heads, 63 sectors/track, 4998 cylinders
Units = cylindres of 16065 * 512 = 8225280 bytes
Identifiant disque: 0xe453466b

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/sdb1               1        2619    21037086   83  Linux
/dev/sdb2            2620        4998    19109317+  83  Linux

Disque /dev/sdc: 200.0 Go, 200049647616 octets
255 heads, 63 sectors/track, 24321 cylinders
Units = cylindres of 16065 * 512 = 8225280 bytes
Identifiant disque: 0xd9ecd9ec

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/sdc1               1       24321   195358401   83  Linux

Disque /dev/sdd: 250.0 Go, 250059350016 octets
255 heads, 63 sectors/track, 30401 cylinders
Units = cylindres of 16065 * 512 = 8225280 bytes
Identifiant disque: 0x393a6f84

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/sdd1   *           1       30401   244196001    7  HPFS/NTFS

here's fstab
proc /proc proc defaults 0 0
# Entry for /dev/sda1 :
UUID=3d3aa6ed-5181-4492-a5e0-f9fc7580689d / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=a6d8506b-586c-453a-a9ff-5ec5ef6b857e none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
/dev/sdb1 /home/macflyz/PicasaDocuments ext3 defaults,auto 0 0
/dev/disk/by-label/P2P /media/p2p ext3 defaults,auto 0 0
/dev/disk/by-label/Sea250 /media/Sea250 ntfs-3g defaults,locale=fr_FR.UTF-8 0 0
/dev/disk/by-label/S200RAID /media/S200RAID ext3 defaults,auto 0 0
/dev/nbd0 /media/MediaDisk ext2 defaults,auto 0 0
/dev/nbd1 /media/BackupDisk ext2 defaults,auto 0 0

in nautilus I get

My home folder
|
System file
|
PicasaDocuments
|
BackupDisk
|
MediaDisk
|
S200RAID
|
Sea250
|
P2P

so I have "PicasaDocuments" appearing as a volume, but it's mounted in my home folder (yeah I finally moved some stuff around mounting only this particular folder in my home dir) so I have my "PicasaDocuments" appearing as a folder in my home directory (that's what I want and I'd like not to see the PicasDocuments volume)

clear enough ?

thx

---

