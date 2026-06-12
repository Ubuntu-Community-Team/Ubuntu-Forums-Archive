---
title: "Hard drive resize screwup"
date: 2008-11-16
forum: General Help
---

### Post by rustyslacker on 2008-11-16
Hi. I tried installing the Fedora 10 preview alongside 8.10 after resizing my root partition (/dev/sda1 is root, /dev/sda2 for swap). At first it didn't recognize Ubuntu, so I added it to the GRUB configs, but then it wouldn't boot. I think it's panicking that there's a bunch of hard drive space gone. 

I broke out my 8.04 live CD to fix the partitions. GParted, after trying to resize /dev/sda1, halts with this:

> GParted 0.3.5

Libparted 1.7.1

Grow /dev/sda1 from 105.10 GiB to 134.40 GiB  00:01    ( ERROR )
     	
calibrate /dev/sda1  00:00    ( SUCCES )
     	
path: /dev/sda1
start: 63
end: 220420158
size: 220420096 (105.10 GiB)
calculate new size and position of /dev/sda1  00:00    ( SUCCES )
     	
requested start: 0
requested end: 281860424
requested size: 281860425 (134.40 GiB)
new start: 63
new end: 281860424
new size: 281860362 (134.40 GiB)
check filesystem on /dev/sda1 for errors and (if possible) fix them  00:01    ( ERROR )
     	
e2fsck -f -y -v /dev/sda1
     	
The filesystem size (according to the superblock) is 35232545 blocks
The physical size of the device is 27552512 blocks
Either the superblock or the partition table is likely to be corrupt!
Abort? yes

e2fsck 1.40.8 (13-Mar-2008)

I tried running "fsck /dev/sda1" manually as root, but it does this after I say "n" to the same "Abort?" question:

```
root@ubuntu:/home/ubuntu# fsck /dev/sda1
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
The filesystem size (according to the superblock) is 35232545 blocks
The physical size of the device is 27552512 blocks
Either the superblock or the partition table is likely to be corrupt!
Abort<y>? no

/dev/sda1 contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Error reading block 27557890 (Invalid argument) while getting next inode from scan.  Ignore error<y>? yes

Force rewrite<y>? yes

Error writing block 27557890 (Invalid argument) while getting next inode from scan.  Ignore error<y>? 

```

I held down the "y" key for a minute or so, and it will ask those same questions for every block. How do I fix my hard drive, OR, barring that, how do I get to my /home folder so I can save my stuff before a fresh 8.10 install? I can't access /home at all for some reason. D:

help :C

---

