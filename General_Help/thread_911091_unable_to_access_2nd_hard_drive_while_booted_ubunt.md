---
title: "unable to access 2nd hard drive while booted ubuntu live cd"
date: 2008-09-05
forum: General Help
---

### Post by deadbeat87 on 2008-09-05
hello im new here:)
im doing a data recovery on my virus/malware ridden second hd(xp restarts automatically about 5 mins after start up)that contains really important documents using ubuntu live cd(transferring from one hd to the other hope it works and my assumption is if the virus/malware is executable in xp it's not in ubuntu). but the problem is, ubuntu cannot detect the second hd, (done the bios and checked it in xp).And i also found out that i have to use grub menu in order to set the parameters so a second harddrive might come up. So far my understanding is i have to install ubuntu in my primary hd which cannot possibly be done because of hd lacks space. so is there a way to access my hd witout doing installing ubuntu or is there another way to restore my documents? any help is appreciated thanx in advance...:)

---

### Post by Elfy on 2008-09-05
Ubuntu doesn't have to be installed on the primary hd.

Grubn gets installed as part of the buntu install 0 it should find your xp and put the option there for it.

Have you looked in places - the partitions/drives should be there, try to open the xp partition.

---

### Post by deadbeat87 on 2008-09-05
> **forestpixie said:**
> 
Have you looked in places - the partitions/drives should be there, try to open the xp partition.

i looked in there but it only shows 21.9gb media(partitioned for xp) and maxtor b(partitioned for random files-my documents used to be there but i moved it when i got a new hd and that hd is the one whose troubled)

---

### Post by Elfy on 2008-09-05
I assume the drive is bigger than that then. Does it show if you do this in a terminal. 

```
sudo fdisk -l
```

Have you tried running antivirus in xp safe mode?

You could install avast from the livecd and then run it on the disc from there.

---

### Post by deadbeat87 on 2008-09-05
already did safe mode scan(used eset SS and kaspersky) and system recovery but it's all the same somehow either the virus didn't show up or the system crashes

hmmm terminal let me try that hope it works

---

### Post by deadbeat87 on 2008-09-05
tried the terminal fdisk somehow it detected the drive
hmmm just curious what're the cahcnes to recover my documents? thanx

---

### Post by Elfy on 2008-09-05
Post the result of the command please

---

### Post by deadbeat87 on 2008-09-05
is there a way to copy the results (from terminal) sorry noob here

---

### Post by Elfy on 2008-09-06
I use the middle mouse button - highlight text interminal then when in reply box use middle button to paste.

---

### Post by deadbeat87 on 2008-09-06
sorry didn't know that there was a terminal app i used the command to go to terminal thats why asked how do i copy lol anyways here's the log 

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa45ca45c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2659    21358386    7  HPFS/NTFS
/dev/sda2            2660        4997    18779985    f  W95 Ext'd (LBA)
/dev/sda5            2660        4997    18779953+   b  W95 FAT32

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xce5afe19

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9729    78148161    7  HPFS/NTFS

---

### Post by Elfy on 2008-09-06
Assuming that the drive your talking about is sdb1 you could try to mount it 

```
sudo mkdir /mnt/windows
sudo mount -t ntfs /dev/sdb1 /mnt/windows
```

It should then be available in nautilus or from the command line.

---

### Post by deadbeat87 on 2008-09-06
did i miss anything?
did the sudo mkdir / mnt/ windows and there was no reply then i tried it again it said something like fiule exists then did following below
ubuntu@ubuntu:~$ sudo mount -t ntfs /dev/sdb1 /mnt/windows
NTFS signature is missing.
Failed to mount '/dev/sdb1': Invalid argument
The device '/dev/sdb1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
ubuntu@ubuntu:~$ sudo mount -t ntfs /dev/sdb1
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .

---

### Post by Elfy on 2008-09-07
Looks like there a definite problems with the drive then - 

> NTFS signature is missing.
Failed to mount '/dev/sdb1': Invalid argument
The device '/dev/sdb1' doesn't have a valid NTFS.

You could try to recover it and/or the data with photorec and testdisk, you can install it on the livecd. I don't know much about the program though I'm afraid.

Some links

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by deadbeat87 on 2008-09-10
did the phtotrecovry and it seems everything is fine now, about 99% of the hd was recovered. (even the virus) anyways evrything is fine now thank you very much

---

### Post by deadbeat87 on 2008-09-10
anyway how do i put a [solve] at the thread header?

---

### Post by Elfy on 2008-09-10
USe the thread tools at the top of the page.

Glad you got back most of your drive.

---

