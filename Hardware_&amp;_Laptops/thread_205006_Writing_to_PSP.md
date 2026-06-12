---
title: "Writing to PSP"
date: 2006-06-27
forum: Hardware &amp; Laptops
---

### Post by kpaul_nyc on 2006-06-27
Hey guys. I am new to Ubuntu (i'm a windows convert). I want to know how to write music and photos to my PSP. I checked the properties and the permission tab it has everything checked for Owner but nothing checked for anything else. I tried to put the check on it but it unchecks immediatly. The PSP automatically loads up. My account is the only account on this computer and I dont understand why it doesnt have privleges to change the permissions on the PSP (i can change them on anything else though).

---

### Post by teaker1s on 2006-06-27
either in console or create a launcher 'gksudo nautilus' this will give you root access in file browser and you will be able to move delete etc without permission problems. you'll find your not the owner and without being sudo root user you can't change them

---

### Post by kpaul_nyc on 2006-06-28
Thanks but when i do that it still says that its a Read-Only disk....

---

### Post by teaker1s on 2006-06-28
okay I'm guessing that it has mounted with read only file permissions, does it mount as a usb drive or something else? not having a psp I know very little about them and how they mount! someone may be able to guide you on how to mount it read write.

I know NTFS xp file systems mount read only due to risk of corruption if you write, I would also suggest you find out what file system the psp has and if it's linux friendly before writing to it just in case

---

### Post by kpaul_nyc on 2006-06-28
The PSP mounts as a music player, with an iPod Nano icon. How do I mount something so it reads AND writes? It automatically mounts. It is connected by USB and it has a memory stick inside it which is used to store music/photos/vidoes.

---

### Post by teaker1s on 2006-06-28
at this point I'm guessing it's 'fat' formatted-can windows see it without any software installed?

have a look at [this]("http://ubuntuguide.org/wiki/Dapper#How_to_mount.2Funmount_Windows_partitions_.28FAT.29_manually.2C_and_allow_all_users_to_read.2Fwrite") 

it will give you an idea of how to mount a partion also look at [this]("https://help.ubuntu.com/community/Mount") which discusses ipod's which are quote "Devices like USB sticks are treated like hard drives (so /dev/sda1, for example, may contain a filesystem) and so are iPods (although I think the main data on an iPod is stored on the second partition)"

I'm an x windows user so my appologies for the quality of the info, I can only point you to information.

you want to unmount the device, then manually mount it-when you can read write you then will need to 'sudo gedit /etc/fstab' so it mounts with correct permissions. Make sure you read thoughly before editing this file and understand.

---

### Post by kpaul_nyc on 2006-06-28
but it automatically mounts

---

### Post by kpaul_nyc on 2006-06-28
Can someone give me a step by step guide on this? Im a total newbie. It automatically mounts and I need help trying to stop that.

---

### Post by teaker1s on 2006-06-29
edited

---

### Post by kpaul_nyc on 2006-06-29
No one knows how to do this?

---

### Post by teaker1s on 2006-06-29
[http://ubuntuguide.org/wiki/Dapper#How_to_mount.2Funmount_Windows_partitions_.28FAT.29_manually.2C_and_allow_all_users_to_read.2Fwrite]("http://ubuntuguide.org/wiki/Dapper#How_to_mount.2Funmount_Windows_partitions_.28FAT.29_manually.2C_and_allow_all_users_to_read.2Fwrite")


**_yours will be sda1_**
How to mount/unmount Windows partitions (FAT) manually, and allow all users to read/write

    * Read #General Notes
    * Read #How to list partition tables 

    e.g. Assumed that /dev/hda1 is the location of Windows partition (FAT) 
    Local mount folder: /media/windows 

    * To mount Windows partition 

sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows/ -t vfat -o iocharset=utf8,umask=000

    * To unmount Windows partition 

sudo umount /media/windows/

---

### Post by KSean on 2006-07-01
I am also having this issue, I've tried searching the forums and nothing I've tried works :\

---

### Post by teaker1s on 2006-07-01
okay I've been thinking about how we find out what file system it has and then we can manually mount and unmount it.

'sudo fdisk -l'  then look for sda1 if your not sure paste output on forum and I'll try to help you

---

### Post by Downtown on 2006-07-03
I'm relatively new to Ubuntu (or Linux in general), but I'm a PSP owner that wanted to find how to manage my PSP files also.  Bear with me if I say something wrong, as I'm still new to Linux terminology.

First, I checked under what attributes Ubuntu read my PSP.  Put your PSP under USB mode, and then in terminal type:
```
sudo fdisk -l
```
It showed mine as /dev/sda1 and FAT16 filesystem.
I created a folder in /media called /usb which I'll use for my other MP3 player as well:
```
sudo mkdir /media/usb
```
So, then I edited fstab:
```
sudo kwrite /etc/fstab
```
and added the line:
```
/dev/sda1	/media/usb	vfat	iocharset=utf8,umask=000	0	0
```
then mount all drives:
```
sudo mount -a
```
For me, the PSP showed up on my desktop as a Removable Disk.  I was then able to read and write any file I wanted to my PSP including music, photos, and gamesaves.
When I'm done I:
```
sudo umount /media/usb
```
to unmount the PSP, then comment out the line I made on fstab:
```
#/dev/sda1	/media/usb	vfat	iocharset=utf8,umask=000	0	0
```
Whenver I need to use it again, just uncomment, and remount.  I'm sure someone can make a script that'll do that automatically, but I'm not that advanced yet.

---

