---
title: "upgraded to 9.10 now hangs at boot"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by kai333 on 2009-10-30
getting this after upgrade to 9.10

Starting up...
Loading, please wait...
Gave up waiting for root device. Common problems:
- Boot args(cat /proc/cmdline)
  -check root delay= (did the system wait long enough?)
  -check root= (did the system wait for the right device?)
- Missing modules (cat /proc/modules;ls /dev)
Alert! /dev/disk/by-uuid/1bd1dd50-835b-4cf6-b590-dbff4c83d446 does not exist Dropping to shell!

BusyBox v1.10.2. (Ubuntu 1:1.10.2-1ununtu7) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)

booted up a usb install on a stick I have and ran fsck got this

root@kai-laptop:/home/kai# sudo e2fsck -fyv /dev/sda2
e2fsck 1.41.3 (12-Oct-2008)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

  175317 inodes used (16.79%)
    5343 non-contiguous inodes (3.0%)
         # of inodes with ind/dind/tind blocks: 8338/161/0
 1545731 blocks used (74.66%)
       0 bad blocks
       0 large files

  126377 regular files
   18581 directories
      68 character device files
      26 block device files
       3 fifos
     527 links
   30231 symbolic links (24325 fast symbolic links)
      22 sockets
any ideas?

---

### Post by ducksoup on 2009-10-30
I've having the same problem.

It seems Grub and the /etc/fstab file are tyring to use UUIDs that no longer exist.  Is there a way to make them exist??

---

### Post by kai333 on 2009-10-30
Mine is really strange the uuid is the right one, no errors on the drive when checked in partition manager when booted off usb stick. pullin my hair out now

---

### Post by AndreLeComte on 2009-11-08
I have the same issue although it only occurs with the 2.6.31 kernel. I can boot Ubuntu 9.10 by using the 2.6.28 kernel. Any solution?

---

### Post by arekku on 2009-11-09
[Here](http://www.dedoimedo.com/computers/ubuntu-initrd-bug.html)

Replace your nonworking initrd file with a previous version. For you Andre all you need to do is (just in case you are new)

cd /boot
sudo mv initrd.img-2.6.31-14-generic backup
sudo cp initrd.img-2.6.28-16-generic initrd.img-2.6.31-14-generic

---

### Post by AndreLeComte on 2009-11-09
arekku, thank you! My system now boots into 2.6.31 using the old initrd.img file.

---

