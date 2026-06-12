---
title: "unable to mount usb stick"
date: 2011-07-04
forum: Hardware
---

### Post by Jouke S on 2011-07-04
I formatted my usb stick to nfts to fit files larger than 4gb (fat32 won't support it) and now I'm unable to mount it.
The drive is visible through Nautilus and GParted but I can't mount it there and the terminal command  'mount /dev/sdh1'
returns 'mount: can't find /dev/sdh1 in /etc/fstab or /etc/mtab'


formatting it to other file systems doesn't do anything 
drive information:
> Disk /dev/sdh: 8032 MB, 8032092160 bytes
5 heads, 32 sectors/track, 98048 cylinders
Units = cylinders of 160 * 512 = 81920 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf4c4f4c4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1   *          51       98048     7839808   83  Linux


terminal command 'lsusb' returns this
> Bus 001 Device 007: ID 0930:6545 Toshiba Corp. Kingston DataTraveler 2.0 Stick (4GB) / PNY Attache 4GB Stick

it's the 8gb version though

---

### Post by xrhettx on 2011-07-04
You're using NTFS on a flash drive in Linux? Try FAT.

---

### Post by Jouke S on 2011-07-04
> **xrhettx said:**
> You're using NTFS on a flash drive in Linux? Try FAT.

Try reading the first sentence 


I've fixed the problem by typing 'gksu gedit /etc/fstab'
and adding '/dev/sdg1 /media/8GB ntfs defaults,auto,uid=1000,gid=1000,umask=000 0 0' to the file 

[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)
there's a tutorial

---

### Post by linuchsan on 2011-07-04
For now it is /dev/sdg1 ...what in the future?
It is appreciated that you send us a link how you "solved it". A lot of people don't do so ;-)

---

### Post by Jouke S on 2011-07-04
> **linuchsan said:**
> For now it is /dev/sdg1 ...what in the future?
It is appreciated that you send us a link how you "solved it". A lot of people don't do so ;-)

it mysteriously migrated to /dev/sdc1 now, what happened we may never know :p

---

### Post by mcduck on 2011-07-04
> **Jouke S said:**
> I formatted my usb stick to nfts to fit files larger than 4gb (fat32 won't support it) and now I'm unable to mount it.
The drive is visible through Nautilus and GParted but I can't mount it there and the terminal command  'mount /dev/sdh1'
returns 'mount: can't find /dev/sdh1 in /etc/fstab or /etc/mtab'


formatting it to other file systems doesn't do anything 
drive information:


terminal command 'lsusb' returns this

it's the 8gb version though

If you haven't defined a drive in fstab, you have to tell mount a bit more than what you are now telling it. You need to specify what to mount, what filesystem it uses, and where you wish to mount it. And you also need to create the mount point if you haven't done that already.

```
sudo mkdir /media/usbdrive
sudo mount -t ntfs /dev/sdf1 /media/usbdrive
```

(if the drive is configured in fstab, you can mount it simply by specifying the drve to mount, ort it's mount point. Mount will get the rest of the required information from fstab)

---

