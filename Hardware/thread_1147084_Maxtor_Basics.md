---
title: "Maxtor Basics"
date: 2009-05-03
forum: Hardware
---

### Post by decay85 on 2009-05-03
My father recently bought a Maxtor Basics external desktop hard drive for me, and put some files into it on his computer (which runs windows xp).

When I got home I plugged it into my computer, and the hard disk popped up, but I'm unable to write any files to in in Unbuntu. It works in Windows, tho.

[This guy here seemed to have the same problem as me]("http://ubuntuforums.org/showthread.php?t=1097784&highlight=maxtor"), so I followed the instructions he was given, and here's what I've got (sorry, but I'm a total noob with this stuff, it doesn't mean anything to me):


> sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80032038912 bytes
255 heads, 63 sectors/track, 9730 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9543    76654116   83  Linux
/dev/sda2            9544        9730     1502077+   5  Extended
/dev/sda5            9544        9730     1502046   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001    7  HPFS/NTFS


df -h

Filesystem            Size Used Avail Use% Mounted on
/dev/sda1              72G   66G  3,3G  96% /
varrun                252M   80K  252M   1% /var/run
varlock               252M     0  252M   0% /var/lock
procbususb             10M  120K  9,9M   2% /proc/bus/usb
udev                   10M  120K  9,9M   2% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   18M  235M   7% /lib/modules/2.6.17-12-generic/volatile
/dev/sdb1             932G   37G  896G   4% /media/usbdisk


It didn't seem like that guy got a final reply...



Remember, I have very little knowledge about this, so try not to get too technical with me. Any help would be most appreciated!!

---

### Post by mikedep333 on 2009-05-03
What version of Ubuntu are you running? Write support for ntfs  (the Microsoft Windows standard partition/filesystem (way of organizing data on a drive)) (like you have on that drive) has only been added somewhat recently.

Also, you might want to check the disk for errors on his Windows computer. I believe you can do that by right clicking on the drive/volume/partition under windows and going to properites or something.

---

### Post by decay85 on 2009-05-03
I think it's 6 something. I'm trying to take a back-up of my files before I update my system, so that I don't lose anything. But since I'm unable to write to this disk, I'm not sure what to do.

---

### Post by drs305 on 2009-05-03
The drive is formatted to NTFS (windows format). The easiest thing to set it up is to run *ntfs-config*, a program that will allow it to boot on startup.

Install the application. Open a terminal (ALT-F2 or Applications, Accessories, Terminal):
```
sudo apt-get install ntfs-config
```
Run *ntfs-config*: System Tools, NTFS Configuration Tool, or:
```
gksudo ntfs-config
```

Select the partition and "Apply". On the right side, type in a mount point between the < >. Whatever you enter will be placed in the /media folder. So if you type *mydata*, the partition will be mounted on /media/mydata. Apply, then choose internal/external.

You can then run the following to mount it:
```

sudo mount -a

```

That's it, and from now on it should be mounted when you boot if it is plugged in. If it's not plugged in at start, plug it in and run the above command if it doesn't automatically mount.

---

### Post by mikedep333 on 2009-05-03
This page explains everything.

[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

Note that if you have Ubuntu 6.06, you need to go out of your way with the instructions there.

If you have Ubuntu 6.10, there have been no more security updates for a year now. I would strongly advise you to upgrade by doing a full reinstall.

The other alternative is to have your father backup all the files on the external drive, and reformat it with FAT32. Windows XP purposely does not let you format large drives with FAT32, so you'll have to format it with FAT32 from Ubuntu Linux. There are instructions for doing this with GPARTED here:
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

---

### Post by decay85 on 2009-05-03
I found out I'm running Unbuntu 6.10. 

I get all the way to installing ntfs-3g, but when I try to install ntfs-config, I get this message:

> ntfs-config:
 Dependent on: libdbus-1-2 (>=0.60) but it is not installable

But from what I can see, I've already got it installed:
[IMG]http://img217.imageshack.us/img217/2184/skjermdump5.png[/IMG]

Also, my computer can't seem to find the packages for libdbus-1-dev, libdbus-glib-1-dev & libdbus-qt-1-dev....

---

### Post by drs305 on 2009-05-03
If you *do* have ntfs-3g installed, you can do what ntfs-config does manually.

Make a mount point. Name it what you want, but use the name throughout this post.
```
sudo mkdir /media/yourmountpoint
```

Back up fstab and open for editing:
```

sudo cp /etc/fstab /etc/fstab.bak
gksudo gedit /etc/fstab &

```

Add this entry:
> 
/dev/sdb1 /media/yourmountpoint ntfs-3g auto,users,uid=1000,utf8,umask=027 0 0

This will make you the owner of the partition when it mounts and you will be able to r/w to it.

I would recommend you use the UUID designation instead of "sdb1". Usually UUIDs won't change, the "sdb1" designation *could*.
To accomplish that, run this:
```

sudo blkid | grep "/dev/sdb1"

```
That will give you the UUID of your sdb1 partition.
Take that code and in fstab replace "/dev/sdb1" with:
> 
UUID=XXXXX-XXXX-XXXX

so the end result looks something like:
UUID=7299e8f1-7caf-4cc3-8a54-cbcba80930 /media/yourmountpoint ntfs-3g auto,users,uid=1000,utf8,umask=027 0 0

---

### Post by mikedep333 on 2009-05-04
Decay85:

Did you attempt to install the Ubuntu 6.06 packages for NTFS-3G and NTFS-config under 6.10? If so, that is your problem.

---

### Post by decay85 on 2009-05-04
It still didn't solve my problem. **Thanks a lot for your help**, tho. I'll just try to get hold of another external hard disk some time soon, take a backup, and simply install the most recent version of ubuntu. This has simply been too much hassle.


EDIT:
> **mikedep333 said:**
> Decay85:

Did you attempt to install the Ubuntu 6.06 packages for NTFS-3G and NTFS-config under 6.10? If so, that is your problem.
I don't think so, I tried installing it using both the regular package handler and synaptic.

---

