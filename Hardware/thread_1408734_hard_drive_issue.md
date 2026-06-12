---
title: "hard drive issue"
date: 2010-02-16
forum: Hardware
---

### Post by MDBailey87 on 2010-02-16
Installed a PCI USB card today and unplugged my hard drives during said installation. Once the card was in I plugged them back in and booted the computer. I have three total internal drives, one with the OS, one for music, and one for movies.  The music drive mounts correctly, but the movie drive appears to have erased the data on it, except the main folders ('Movies', 'Recycled') and the only folder within Movies is 'No Country For Old Men' but there is nothing in that folder.

If I try to create a folder I get this message:
     Error while creating directory untitled folder.
     There was an error creating the directory in /media/VIDEO.
     Error creating directory: Input/output error

The properties also show Free Space as "Unknown"...

I'm somewhat of a newbie with linux and am unsure of what I did to cause this, or if theres even a way to recover my data, any ideas?

---

### Post by MDBailey87 on 2010-02-17
bump

---

### Post by davec64 on 2010-02-17
It looks to me that the system is having a problem mounting the disk. 
/media/VIDEO is the mount point and not the disk, so in english that means that a command is issued to mount the disk under /media/VIDEO, you can then acces the disk under this location.
As it appears to partially mount and you're unable to create a folder, I would try running fsck.

To determine which disk it is:
```
sudo fdisk -l
```

Unmount the disk 
```
sudo umount /dev/<DISK>
```(replace DISK with he correct name e.g. /dev/sdb1)

Then run fsck
```
sudo fsck /dev/<DISK>
```If any files are recovered you will find them in /home/lost+found.
With a bit of luck that may not be necessary!

Hope that helps! :)

---

### Post by MDBailey87 on 2010-02-21
Thanks for the reply, been busy at work past few days, haven't had a chance to work on it til now...  here's what I get:

"sudo fdisk -l"
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60801   488384001    c  W95 FAT32 (LBA)
```

so when I run "sudo fsck /dev/sda1" I get
```
fsck from util-linux-ng 2.16
dosfsck 3.0.3, 18 May 2009, FAT32, LFN
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  67:6b/54, 68:96/1f, 69:51/fb, 70:5d/16, 71:56/4d, 72:49/79, 73:44/20
  , 74:45/42, 75:4f/6f, 76:20/6f, 77:20/6b
1) Copy original to backup
2) Copy backup to original
3) No action
? 2
Got 9535488 bytes instead of 61033100 at 16384
```

Same thing if I choose option 1.  Another thread I came across mentioned trying these commands for FAT32 systems, sudo dosfsck /dev/sda1
sudo fsck.vfat /dev/sda1
But result in
```
dosfsck 3.0.3, 18 May 2009, FAT32, LFN
Read 512 bytes at 0:Input/output error
```

Also I can view everything if I 'dir' while in /media/VIDEOS/Movies, it displayed all the folders, but not when in Nautilus.  Another strange thing happened today when I booted up.... the drive was working fine, took forever to mount, but all my files were there. Unfortunately it was the only hard drive I had plugged in at the time so all I could do was burn a few discs worth before the drive crashed again and I could no longer view anything.

---

