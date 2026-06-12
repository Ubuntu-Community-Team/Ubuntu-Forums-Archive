---
title: "Can not wirte to usb attached external HD"
date: 2011-09-03
forum: Hardware
---

### Post by speed32219 on 2011-09-03
I have a usb attahced ext HD that I can not write to from XP across the network.  I can use putty, log in and have full access, but also some locally running programs on Ubuntu fail to write also.  I have exhausted all my known options currently, and I hope someone here can put me on the right track.

ubuntu 10.10

$ fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d4a40

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1275    10240000   83  Linux
/dev/sda2            1275       30223   232517632   83  Linux
/dev/sda3           30223       30402     1439744   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf6f41f03

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001   83  Linux

mount
/dev/sdb1               1      121601   976760001   83  Linux^C
$ mount

/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /var/lib/ureadahead/debugfs type debugfs (rw,relatime)
/dev/sda2 on /home type ext3 (rw)
/dev/sdb1 on /media/Digital_Content type ext3 (rw,nosuid,nodev,uhelper=udisks)

$ ls -al  
total 68
drwxrwxrwx 17 User1 User1 4096 2011-09-03 17:09 .
drwxrwxrwx  3 User1 User1 4096 2011-09-03 12:43 ..
drwxr-xr-x  2 User1 User1 4096 2011-07-07 08:36 2011-07-07-12-DS-Root-img
drwxr-xr-x  2 User1 User1 4096 2011-08-23 13:53 2011-08-23-17-JW_img
drwxr-xr-x  2 User1 User1 4096 2011-08-29 08:54 8_29_11_JW_CPSBSAB_IMG
drwxrwxrwx 24 User1 User1 4096 2011-09-03 02:44 Blu_Ray
drwxrw-rw-  7 User1 User1 4096 2011-08-03 21:09 Convert
drwxrwxrwx  4 User1 User1 4096 2011-09-03 13:03 Downloads
drwxrwxrwx  4 User1 User1 4096 2011-07-09 12:39 Movies
drwxrwxrwx 30 User1 User1 4096 2011-09-03 13:03 Music
drwxrwxrwx 17 User1 User1 4096 2011-09-02 23:39 Music_Videos
drwxrwxrwx  4 User1 User1 4096 2011-07-04 19:53 Pictures
drwxrwxrwx  6 User1 User1 4096 2011-09-03 01:15 TV_Shows

If I use windows explorer and try and move files from the internal HD (dev/sda1) to /media/Digital_Content/ external HD, I get a write permission error.  But I can add/move/delete any files from the internal HD (dev/sda1)including moving files from the external dirve to the internal dirve.  I can not create/add/move/delete  files with the external usb attached HD using windows exporler.  If I use putty, no problem, but like I stated, some locally run apps on ubuntu can not write to the external drive also. 

Any suggestions welcome.

---

### Post by infested999 on 2011-09-03
So the external HD is mapped as a network drive and you are trying to write to it from a diffrent computer on the network?

The other computer that is running Windows, are you using the "My Network Places" folder to access the external HD or are you using PuTTy to try to transfer the files.

---

### Post by gordintoronto on 2011-09-03
Sorry, my idea was irrelevant.

---

### Post by speed32219 on 2011-09-04
> **infested999 said:**
> So the external HD is mapped as a network drive and you are trying to write to it from a diffrent computer on the network?

The other computer that is running Windows, are you using the "My Network Places" folder to access the external HD or are you using PuTTy to try to transfer the files.



In so many words, yes.  

gordintoronto
"Sorry, my idea was irrelevant."  Let me decide, all help is greatly appreciated!  I'm really in a bind with this, been checking samba conf files, sudoers, etc.  Still no joy.

I'm baffled that I can write to it (Ubuntu server/pc Internal drives) using my windows networked PC  but can not write to the external attached Hard drive (attached to ubunut server/pc) using windows explorer or my network places.  BUT, if I use putty/ssh (Windows machine) I can do anything I want with it.

---

