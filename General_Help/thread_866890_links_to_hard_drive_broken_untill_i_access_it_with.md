---
title: "links to hard drive broken untill i access it with nautilus"
date: 2008-07-22
forum: General Help
---

### Post by beholdforiambob on 2008-07-22
Sorry about the ambiguous thread title but half of the problem stems from the fact that I don't know what the problem is.


I have 3 hard drives on my computer, one for Linux one for Windows and one for shared media.

The first problem is that I have links to folders in the drive under the places tab. Whenever I start Ubuntu these links are broken.

The second problem (and perhaps most annoying) is that all of my music is stored on the media drive and if i open Rhythmbox it removes all of my music from the play list (and when your music collection is over 6149 songs the process takes a while)

{I stopped using Banshee all together because it would mark the files as errors and then load a copy of them all again. at one point I had 10 copies of each song where only one of them worked at that point I had 61490 songs and every time I went to clear the list Banshee would frees due to the shere volume of items.}

once I access the drive via nautilus by clicking on the link to the drive in places, everything works fine. 

I know it is not a bug but another one of those security measure or lack of rights things but it is driving me nuts.

---

### Post by Potatoj316 on 2008-07-22
Correct!  The hard drive does not get mounted until you tell it to mount (ie accessing from places menu)  You could write a script (like 1 line) that looks something like this
```
sudo mount /dev/hdc1 /MOUNTPOINT
```
(might be hda1 or hdb1) (mountpoint could be something like /media/shareddisk) then have the script run on bootup or login

---

### Post by drs305 on 2008-07-22
Another alternative is to place an entry in /etc/fstab so that the drive/partition is mounted automatically at startup. If it is already listed there you may have to change some of the options.

If you don't know how to do this, post the results of:
```

sudo blkid
sudo fdisk -l
cat /etc/fstab

```

I'm off but someone will surely help or you can do a search on the forum for how to edit fstab.

---

### Post by beholdforiambob on 2008-07-22
Wow that was a quick response!

Potato, how or where do i write this code? I assume I don't just copy paste into the command line.




DRS305 here is the stuff you needed.

> beholdforiambob@beholdforiambob-desktop:~$ sudo blkid
[sudo] password for beholdforiambob: 
/dev/hda1: UUID="06562c27-4840-4db7-80af-f6a84d9d8df1" TYPE="ext3" 
/dev/hda5: TYPE="swap" UUID="9d79e382-af7e-47ad-9669-ef593abdc514" 
/dev/sda1: UUID="94548D89548D6F34" TYPE="ntfs" 
/dev/sdb1: UUID="A8445BF8445BC828" LABEL="storage" TYPE="ntfs" 
/dev/hda2: LABEL="HP_RECOVERY" UUID="4429-F2CD" TYPE="vfat" 
beholdforiambob@beholdforiambob-desktop:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9729    78148161    7  HPFS/NTFS

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xffe4ffe4

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        8021    64428651   83  Linux
/dev/hda2   *        8022        9197     9446220    b  W95 FAT32
/dev/hda3            9328        9729     3229065    5  Extended
/dev/hda5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x16e7c944

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641    7  HPFS/NTFS
beholdforiambob@beholdforiambob-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=06562c27-4840-4db7-80af-f6a84d9d8df1 /               ext3    relatime,errors=remount-ro 0       1
# /dev/hda5
UUID=9d79e382-af7e-47ad-9669-ef593abdc514 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
beholdforiambob@beholdforiambob-desktop:~$ 
beholdforiambob@beholdforiambob-desktop:~$ 


---

### Post by oliov on 2008-07-23
Hi beholdforiambob,

Cool handle by the way.

From a felow Ubuntu n00b to another, i just had this prob, and the solution to it can be found right [here]("https://help.ubuntu.com/community/InstallingANewHardDrive#Automatic%20Mount%20at%20Boot") in the forums in a post about mounting a new hard drive.   You should use the info you got from 'blkid'

happy hunting!

oli

---

### Post by iaculallad on 2008-07-23
Say, it's the /dev/sdb1 (labeled as **Storage**) that needs to be auto-mounted:

First thing to do is to install ntfs-3g driver.

```
sudo apt-get install ntfs-3g
```

Then, create the mount point for that device:

```
sudo mkdir /media/musicdrive
```

Open /etc/fstab file for editing:

```
gksudo gedit /etc/fstab
```

and add the line of code below to the last part of the file:

> /dev/sdb1 /media/musicdrive ntfs-3g defaults 0 0

Save and Close the File: Drop to your terminal and issue the command:

```
sudo mount -a
```

So, everytime you start your computer, sdb1 will automatically be mounted.

---

### Post by beholdforiambob on 2008-07-24
Thanks every one!


****************Ignore the following unless your lookin for a good laugh**************

**************************************************************************************
            My fault I am dyslexic I was spelling e*tc* as e*ct*  
**************************************************************************************

I have run in to a bit of trouble however. I a ran the command 

```
gksudo gedit /etc/fstab
```

and a document popped up, however it was blank. I inserted the command 
```
/dev/sdb1 /media/musicdrive ntfs-3g defaults 0 0 
```
anyway and when I went to save I got the message

Could not save the file /ect/fstab.
Unexpected error: File not found

I have done a little bit of reading and digging with the information you guys gave me (thanks) and I have learned a lot but it seems I have hit a roadblock.

BTW when I run
```
cat /ect/fstab
```

I get this answer

```
cat: /ect/fstab: No such file or directory
```

---

### Post by Potatoj316 on 2008-07-24
make sure your typing /etc/fstab and not /ect/fstab, you made that mistake once when typing here

EDIT: Ok, you got it while I was writing this

---

### Post by beholdforiambob on 2008-07-24
All Right!

I got it to work. a couple of notes though. 
iaculallad had me make a mount point for my drive.via
```
sudo mkdir /media/musicdrive
```
however my drive already had a mount point labeled /media/storage. from what I understand this step is used when a drive does not have an existing mount point.

for those of you who are in the same situation you can find the name of your drives mount point via nautilus by navigating to the folder file system/media

If your problem is that your drive (any separate drive than the one Ubuntu is on) will not automatically mount with out you navigating to it via nautilus follow these steps.

find out the logical name for your drive by typeing this into the command line 

```
sudo lshw -C disk
```

then, as iaculallad said, open fstab by typing this into the command line

```
gksudo gedit /etc/fstab
```

at the end of the document (fstab) enter this code

```
{the logical name of your drive} /media/{the mount point name of your drive} ntfs-3g defaults 0 0 
```

finally either enter this command to mount the drive 
```
sudo mount -a
```



Thanks to every one for all the Ubuntu Love. this is the first real fix I have done on my own. (that is with out my brother in law stepping in and fixing it for me.)

---

### Post by alexe5 on 2010-07-20
Hey i ran this command. but how can i undo it?
 	Code:
 	sudo apt-get install ntfs-3g 
Then, create the mount point for that device:

 	Code:
 	sudo mkdir /media/musicdrive 
Open /etc/fstab file for editing:

 	Code:
 	gksudo gedit /etc/fstab 
and add the line of code below to the last part of the file:

 	Quote:
 	 	 		 			 				/dev/sdb1 /media/musicdrive ntfs-3g defaults 0 0 			 		 	 	 
Save and Close the File: Drop to your terminal and issue the  command:

 	Code:
 	sudo mount -a

---

