---
title: "Live usb 11.04 unable to mount sda ntfs after editing fstab code 16"
date: 2011-10-23
forum: Hardware
---

### Post by Shaggin Shea on 2011-10-23
I use live usb ubuntu 11.04 and was attempting to edit fstab to mount my ntfs sda1 drive on boot up. This is the guide I used [http://ubuntuguide.org/wiki/Ubuntu:Oneiric#Mounting_NTFS_Partitions_.28with_read.2Fwrite_privileges.29](http://ubuntuguide.org/wiki/Ubuntu:Oneiric#Mounting_NTFS_Partitions_.28with_read.2Fwrite_privileges.29)

So here is my 

sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
240 heads, 63 sectors/track, 64601 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       62670   473785168+   7  HPFS/NTFS
/dev/sda2           62671       64601    14598360    7  HPFS/NTFS

Disk /dev/sdb: 8019 MB, 8019509248 bytes
20 heads, 16 sectors/track, 48947 cylinders
Units = cylinders of 320 * 512 = 163840 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008b1a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       48948     7831512    c  W95 FAT32 (LBA)

I then did this 
sudo nano /etc/fstab

and added this line under the fstab
/dev/sda1 /media/WindowsNTFS ntfs-3g quiet,defaults,rw 0 0

Restarted the computer

So now it does not appear my drive mounts on boot up and instead when I try to open my drive through the file manager I get 

Unable to mount location
Error mounting: mount exited with exit code 16: Mount is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command.
When I check fstab the edit I made is no longer there
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0

---

### Post by Shaggin Shea on 2011-10-29
I did fuser -m /dev/sda1 and this is what is returned

ubuntu@ubuntu:~$ sudo fuser -m /dev/sda1
Cannot stat file /proc/4212/fd/21: Stale NFS file handle
Cannot stat file /proc/4212/fd/22: Stale NFS file handle

ls -al /dev/sda1
brw-rw---- 1 root disk 8, 1 2011-10-29 09:52 /dev/sda1

---

### Post by Shaggin Shea on 2011-11-01
Does this help diagnose the problem.

ubuntu@ubuntu:~$ ls -l /media
total 8
drwx------ 2 root root 4096 2011-10-22 22:23 casper-rw
lrwxrwxrwx 1 root root    6 2011-08-17 12:48 cdrom -> /cdrom
drwxr-xr-x 2 root root 4096 2011-10-22 22:13 WindowsNTFS
ubuntu@ubuntu:~$ mount WindowsNTFS
mount: can't find WindowsNTFS in /etc/fstab or /etc/mtab
ubuntu@ubuntu:~$ ls -l /media/WindowsNTFS
total 0

---

### Post by Shaggin Shea on 2011-11-03
Please delete because I have moved this question to general as I was getting no help here (guessing it was my fault for putting it in the wrong place)

---

