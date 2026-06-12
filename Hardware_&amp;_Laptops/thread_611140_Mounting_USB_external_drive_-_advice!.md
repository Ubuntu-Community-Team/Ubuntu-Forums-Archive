---
title: "Mounting USB external drive - advice!"
date: 2007-11-12
forum: Hardware &amp; Laptops
---

### Post by Giradman on 2007-11-12
I have Ubuntu 7.1 running on an older IBM laptop (TP X40) - one partition on a new HD - also own a Transcend Storejet 1.8, 20 GB which I used on the same IBM w/ Windows XP previously - want to use it for backup on the IBM w/ Ubuntu, but have been completely frustrated getting this drive to be recognized when plugged into a USB port.

Intermittently the drive is 'recognized' but @ other times, nothing shows up on the desktop and I cannot accessed the drive; after 4 attempts, Transcend has finally responded to my e-mails - below a part of their message indicating that I need to 'mount' the drive - I created the 'new' directory in mnt using the sudo command; tried to use their mounting example w/o success; when the drive is recognized by Ubuntu, it seems to be referenced in the /media directory.

Can anyone help me in getting this drive to appear consistently when plugged in?  Thanks for any comments & help - :( 

> Driver Installation for Linux™ Kernel 2.4, or Later
No drivers are required. Plug your StoreJet™ 1.8 into a USB port and mount it.

1. First create a directory for the StoreJet™ 1.8.

Example: mkdir /mnt/Storejet

2. Then, mount the StoreJet™ 1.8.

Example: mount –a –t msdos /dev/sda1 /mnt/Storejet

---

### Post by taurus on 2007-11-12
What's the output of this command from a terminal, after you've plugged in the USB drive?

```
sudo fdisk -l  <-- Lower case letter l, not number 1.
```

---

### Post by Giradman on 2007-11-12
> **taurus said:**
> What's the output of this command from a terminal, after you've plugged in the USB drive?

```
sudo fdisk -l  <-- Lower case letter l, not number 1.
```

**Taurus** - thanks for your response; I plugged in the Transcend drive, which this time was NOT recognized (seems to be a half & half chance?) - perform the above, the return is quoted below - hope that you can help - thanks, again - Dave

> david@ubuntu:~$ sudo fdisk -l
[sudo] password for david:

Disk /dev/sda: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007390c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2342    18812083+  83  Linux
/dev/sda2            2343        2432      722925    5  Extended
/dev/sda5            2343        2432      722893+  82  Linux swap / Solaris

---

### Post by Giradman on 2007-11-12
**Taurus** - just another quick post - I removed & then re-plugged the drive into the USB port - this time the Transcend drive WAS recognized, so I re-did your suggestion which returned the quote below, slightly different, but this time there is a terminal report of this drive w/ & w/o being recognized by the OS - not sure if this helps, but I guess may be instructive - thanks again for all of your help - Dave :)

> david@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007390c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2342    18812083+  83  Linux
/dev/sda2            2343        2432      722925    5  Extended
/dev/sda5            2343        2432      722893+  82  Linux swap / Solaris

Disk /dev/sdb: 20.0 GB, 20003749888 bytes
64 heads, 32 sectors/track, 19077 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19077    19534832    b  W95 FAT32
david@ubuntu:~$ 


---

### Post by taurus on 2007-11-12
Is it ntfs filesystem?  Can you read it from windows?  Maybe you want to run a scandisk on that USB drive to make sure everything is still good.

Then, connect it to back to Ubuntu and see if the system either automounts it or at least detects it in "sudo fdisk -l".

---

### Post by daengbo on 2007-11-12
How old is this drive? If it's being recognized intermittently, there might be a problem with the drive, the housing, or the USB cord. Try switching out the cord. Try the drive on another computer with a different OS and determine whether it has the same symptoms or not. If there is no strange behavior on another computer in several attempts, you can safely assume the problem is in Ubuntu's DBUS or Gnome-VFS.

You might also try mounting with "-t vfat" instead of "-t msdos"

Best of luck.

---

### Post by Giradman on 2007-11-13
Thanks guys for your responses - sorry for the delay but had a long day @ work & just got home! 

The Transcend USB 2.0 drive is about 3 yrs old - this worked fine on my IBM laptop w/ XP - used to transfer my document files only for backup.

I have plugged this drive into 2 XP computers (office & home DTops) - drive is recognized, I can see the files fine in Explorer - the file system is FAT32 - I scanned the disc for errors w/ no problems found; thus, assume the cable is fine, also.

Now, the mounting command provided by Transcend stated 'an example' - I'm just learning the BASH Shell, so not sure 'how correct' this command may be?  Also, when the drive is recognized, it is place in a different directory (described above) - not sure 'what' this means?

Hope some of this info helps - I do have a newer & larger Iomega external drive that works fine w/ this Ubuntu install, so not critical - just irritating that I can't get this older drive to work!  Dave

---

### Post by Giradman on 2007-11-14
Well, still working on trying to consistently install this Storejet USB drive - plugged it in this morning w/o a response; so, did some more reading & web searching - using the dmesg command the drive was present and listed as 'sdb1; I then attempted to mount the drive:  sudo mount -t vfat -o umask=000 /dev/sdb1 /mnt/Storejet (the last directory as defined in my orginal post) - to my SHOCK, the command worked and indeed the Storejet's file system was listed in /mnt/Storejet; unfortunately, no icon appeared on the desktop nor in Nautilus for me to unmount - so, just pull the drive out!

Being persistent, I plugged it back in and the OS this time recognized the Storejet & placed an icon on the desktop - the file system was, however, mounted in /media/disk, but works there fine - I ran another sudo fdisk -l (quoted below); the output  does look different - I've pulled & re-plugged two more times w/ the same results - not sure if this is a 'fix' nor what may have been the solution (if indeed this is long term), but looks better at the moment - thanks all for the help! :)


> Disk /dev/sda: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007390c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2342    18812083+  83  Linux
/dev/sda2            2343        2432      722925    5  Extended
/dev/sda5            2343        2432      722893+  82  Linux swap / Solaris

Disk /dev/sdb: 20.0 GB, 20003749888 bytes
64 heads, 32 sectors/track, 19077 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19077    19534832    b  W95 FAT32
david@ubuntu:/$ 

---

### Post by taurus on 2007-11-14
How about

```
sudo mkdir /media/sdb1
sudo mount -t vfat /dev/sdb1 /media/sdb1 -o iocharset=utf8,umask=000
ls -la /media
```

---

### Post by Giradman on 2007-11-15
> **taurus said:**
> How about
```
sudo mkdir /media/sdb1
sudo mount -t vfat /dev/sdb1 /media/sdb1 -o iocharset=utf8,umask=000
ls -la /media
```

**Taurus** - thanks for the additional information; I plugged the Transcend drive into the laptop several more times after my previous post, both times the drive was recognized and mounted w/ a desktop icon; thus, after a half dozen attempts, seems to be working as expected - I'll hope that the OS has now setup  the drive properly.  Thanks again - Dave

---

