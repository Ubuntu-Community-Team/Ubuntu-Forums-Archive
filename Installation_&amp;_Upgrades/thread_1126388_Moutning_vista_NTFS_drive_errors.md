---
title: "Moutning vista NTFS drive errors"
date: 2009-04-15
forum: Installation &amp; Upgrades
---

### Post by tamas305 on 2009-04-15
I have an external NTFS Hard Drive and whenever I try to mount that partition from Ubuntu it gives an error. Something about an unclean shut down and it advises me to boot into Vista and safely eject the hard drive and shut down correctly.

I was thinking about reformatting the hard drive to be fat32. Are there any better solutions than these two?

Thanks in advance
-tamas

---

### Post by taurus on 2009-04-15
Make sure you unmount it using the _safely remove hardware_ option at the bottom right corner when you use that external drive in windows.  Don't just unplug it from the computer when you are done with it.  Even if you format it to fat32, you still need to unmount it first before you unplug it.

---

### Post by jbrown96 on 2009-04-15
This problem happens when you don't "Safely Remove" it from Windows or unmount it from Ubuntu before removing it. There are two ways around it.

1) Force mount. Not the best idea; it could be a little risky.

2) Use ntfsfix. You will need to install the program ```
sudo apt-get install ntfsprogs
```

Then the syntax is ```
sudo ntfsfix DEVICE
``` where device is of the form /dev/sdXY where X is a letter {a,b,c...} and Y is a number {1,2,3...}. You can make sure what your device is by running ```
sudo fdisk -l
``` but it will probably be /dev/sdb1.

NTFS is probably a better choice than Fat32. NTFS can support larger files (>4GB), has a better journal, doesn't fragment as much, and is better on Windows. If you are only using the drive on Linux, I would recommend Ext3 or XFS. Ext3 is the default file system and is the safe bet. I've always liked XFS; it's very fast, and I've never had any problems with data loss. ReiserFS is getting pretty old and doesn't have good performance any more; JFS is a huge problem -- I've never lost data, but every unclean unmount requires the journal to be recovered, and it's no faster than XFS. If you are going to upgrade to 9.04 (April 23rd!), then go with Ext4.

---

### Post by tamas305 on 2009-04-15
I have Ubuntu installed on a USB drive (full install) and I wanted to access that external NTFS drive from both linux and windows. Does windows recognize ext3? XFS? 

Thanks
-tamas

---

### Post by taurus on 2009-04-15
No, windows will not.  However, you can use fs-driver to access ext2/ext3 filesystem in windows.

[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by jbrown96 on 2009-04-15
I don't think that there is a XFS driver, but there is a Ext2/3 (don't use 2 it doesn't have journaling) driver available [here]("http://www.fs-driver.org/")

---

### Post by tamas305 on 2009-04-15
It is a large drive (500 gb) so is ext3 going to be fast enough for it? or should I just stay with NTFS?

-tamas

---

### Post by taurus on 2009-04-15
If you want to share it between Ubuntu and windows, then stay with ntfs.  Just remember to _unmount_ it first before you unplug it each time you're done using it.

---

### Post by tamas305 on 2009-04-15
That is a pain. However, just wondering, what is the best type of file system that Windows Vista, Ubuntu, (and maybe even OS X) can share. Like for example during a tri-boot.

like one large hard drive partition this way
|vista OS stuff|mac OS X stuff|Ubuntu OS stuff|shared media storage space|

Respectively 100 gb, 90 gb, 10gb, 440gb

Thanks in advanced
-tamas

---

### Post by sahabcse on 2009-04-15
For mounting NTFS/FAT32 file system pls follow below url

[http://sahabm.blogspot.com/2009/03/mount-ntfs-fat32-windows-drive-in.html](http://sahabm.blogspot.com/2009/03/mount-ntfs-fat32-windows-drive-in.html)

---

### Post by jbrown96 on 2009-04-15
FAT32 is compatible across all three OSes. I'm not sure whether OS X can mount NTFS but if you are just using Vista and Ubuntu, it would be much easier (and saves disk space) to forgo the Fat32 partition. You could just have all of the shared data in a folder on the Vista partition and then mount that in Ubuntu. You could even add it to fstab to automount if you use the files a lot. 

This is a [good guide]("http://ubuntuforums.org/showthread.php?t=283131") on fstab

---

### Post by tamas305 on 2009-04-15
> **taurus said:**
> If you want to share it between Ubuntu and windows, then stay with ntfs.  Just remember to _unmount_ it first before you unplug it each time you're done using it.

Is there any way to automatically unmount an external hard drive in a similar way the internal hard drive is? So if you shut down the computer vista/linux will unmount the external drive before closing shop.

-tamas

---

### Post by taurus on 2009-04-15
If you shut down your machine before you remove your external harddrive, the system will unmount it for you.  The problem is while the machine is still running, you just unplug the drive before you unmount it.  That's the problem.

---

### Post by tamas305 on 2009-04-15
For some reason if I just unplug the external drive (no safely remove hardware) then windows does not unmount it correctly...does the option where you disable caching work? Also if I do run a tri-boot of windows vista, Ubuntu and mac os x then what should the shared file system be? Does mac OS X recognize NTFS?

Thanks in advance for your help
-tamas

---

