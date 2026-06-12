---
title: "Bought a hard drive enclosure but not mounting"
date: 2008-10-22
forum: General Help
---

### Post by rapattack1 on 2008-10-22
Hi I bought a hard drive enclosure today as someone gave me a 160gig hard drive(sata) but it won't mount. As soon as I put the hard drive in I connected it to my windows machine and I formatted the 2 partitions on the drive. Silly me didn't know that because I was doing it within windows it wasn't like formatting normally using a command. I have never formatted an external drive apart from a floppy so I am not sure now that I have connected it up to linux what do I do? Ubuntu sees the drive but does not want to mount it. I don't know if I am supposed to execute a command or go back and format it via windows. I will use this device to back up both machines as they have 40gig hd's each and I will in the future(when I get damn Jack working :confused: ) be making audio/video files.

---

### Post by fooman on 2008-10-22
when its plugged in (and powered on, if it has an on/off switch),  does it show up under places?

if yes...what happens when you click on it?

---

### Post by rapattack1 on 2008-10-22
Yes it does show up but I get an error when I click onto the two partitions. I renamed them in windows and they are EXTERNAL and external1. Now after doing this:
root@carla-desktop:~# mkdir /mnt/usbdrive
root@carla-desktop:~# mount /dev/sda1 /mnt/usbdrive

EXTERNAL opens but not external1. EXTERNAL is a smaller partition than external1.

---

### Post by fooman on 2008-10-22
please run the following in a terminal and post back with the output (with the external plugged in and powered on):

```
sudo fdisk -l
```

---

### Post by rapattack1 on 2008-10-22
carla@carla-desktop:~$ sudo fdisk -l

Disk /dev/sda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x80f580f5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4787    38451546   83  Linux
/dev/sda2            4788        4998     1694857+   5  Extended
/dev/sda5            4788        4998     1694826   82  Linux swap / Solaris

Disk /dev/sdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000581ea

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         243     1951866    5  Extended
/dev/sdb2             244        2434    17599207+  83  Linux
/dev/sdb5               1         243     1951834+  82  Linux swap / Solaris

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
240 heads, 63 sectors/track, 20673 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x91e2b08d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         576     4354528+   b  W95 FAT32
/dev/sdc2   *         577       20672   151925760    7  HPFS/NTFS
carla@carla-desktop:~$

---

### Post by scouser73 on 2008-10-22
Hello, did you unmount the drive in Windows correctly, because if you haven't it's counted as an unclean install.  What you need to do is go back into Windows, plug the drive in and then, you'll see a small item in the bottom right hand of the screen **Safely Rmove Hardware**, once you have clicked that, unplug the drive, go back into Ubuntu and it should be working correctly now.

---

### Post by rapattack1 on 2008-10-22
I don't remember if I did that originally but i did it just now and sorry but it didn't work.
What do you mean by unclean install btw? I didn't install anything. Was I supposed to install an os?

---

### Post by scouser73 on 2008-10-22
My apologies, by unclean install, I meant the hard drive. I'm sorry for any confusion.

---

### Post by rapattack1 on 2008-10-22
Oh ok! I am not sure what to do now.

---

### Post by Bluebell392 on 2008-10-22
```
Disk /dev/sdc: 160.0 GB, 160041885696 bytes
240 heads, 63 sectors/track, 20673 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x91e2b08d

Device Boot Start End Blocks Id System
/dev/sdc1 1 576 4354528+ b W95 FAT32
/dev/sdc2 * 577 20672 151925760 7 HPFS/NTFS
```

You need to try to mount /dev/sdc, not /dev/sda1. Also, specify the type of filesystem using the -t flag with mount. (For example, to mount the second partition, you would use mount -t ntfs /dev/sdc2 /somewhere, replace somewhere with the actual mount point.)

---

### Post by shaggy999 on 2008-10-22
To elaborate upon the previous post (just in case you don't know how to do this):

```

cd /media
sudo mkdir fatdrive
sudo mount -t vfat /dev/sdc1 /media/fatdrive

sudo mkdir ntfsdrive
sudo mount -t ntfs-3g /dev/sdc2 /media/ntfsdrive

```

For all FAT partitions you want to use the **vfat** option and for NTFS volumes you want to use **ntfs-3g** if you want to be able to *both* read and write.

---

### Post by rapattack1 on 2008-10-23
shaggy999-Sorry I am really not clear what you are instructing me to do. I know what ntfs and fat partitions are but don't know what the difference is really. I know they exist but their purpose is not clear to me. With the commands are they two different lots for choosing to format in either ntfs or fat? Shouldn't I delete the partition? 

Bluebell392- I don't know. I tried to mount both by clicking onto the icons wherever I stated they are. Sorry I can't remember right now as I am dealing with another computer problem now.
Sorry can you specify what the mount point is? Or give me an example?

Well I tried this :
carla@carla-desktop:~$ cd /media
carla@carla-desktop:/media$ sudo mkdir ntfsdrive
[sudo] password for carla: 
carla@carla-desktop:/media$ sudo mount -t ntfs-3g /dev/sdc2 /media/ntfsdrive
ntfs-3g: Failed to access volume '/dev/sdc2': No such file or directory
Please type '/sbin/mount.ntfs-3g --help' for more information.
carla@carla-desktop:/media$

---

### Post by rapattack1 on 2008-10-25
Oh hang on I didn't have the drive on....but what?! It mounted!!!! :popcorn:
Oh wow. Well I gave it two goes to make sure but now it has worked. I did format both partitions in windows earlier so maybe that is what did the trick. Wish it was only one drive though. I can't work out how to delete the partition.

---

