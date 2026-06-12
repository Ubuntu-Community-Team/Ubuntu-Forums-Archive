---
title: "Ubuntu 8.04 Partition Grub 1.5 error 24, filesystem unknown, unmountable"
date: 2009-06-13
forum: Hardware
---

### Post by Moschti on 2009-06-13
Hello all,

                I have been using Ubuntu for a couple of years now, but this is the first time this error has occured, here are the details.

I left my laptop to download some stuff over night, in the morning i find out that the desktop is not responding. so i switch off the laptop from the button and restart.

when it was starting, i got this error:

Grub stage1.5
error 24

So i plugged in the ubuntu 8.04 live cd and tried the following solutions:

1.  
grub> find /boot/grub/stage1

Error 15: File not found

also tried

grub> find /grub/stage1

Error 15: File not found

2.  i tried this command 

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
240 heads, 63 sectors/track, 15505 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x64656469

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        6008    45420448+   7  HPFS/NTFS
/dev/sda2            6009       15505    71797320   83  Linux

3.  also tried mounting the partition like this:

root@ubuntu:/home/ubuntu# sudo mkdir /media/old
root@ubuntu:/home/ubuntu# sudo mount /dev/sda2 /media/old
mount: you must specify the filesystem type

4.  tried using Gnome Partition Editor:

its shows my windows partition which is dev/sda1   and the file system is ntfs

but then the partition with ubuntu says

/dev/sda2   filesystem unknown   
with more information it says:

unable to detect filesyste! possible reasons are:
the filesystem is damaged
the file system is unknown to Gparted
there is no file system available(unformatted)


5. My friend also suggested i try the following:

grub> root (hd0,1)
grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... no

Error 24: Attempt to access block outside partition

grub> root (hd0,2)

Error 22: No such partition


Any Help would be greatly appreciated. My Masters thesis is on that partition and i havent updated my external hard disk version for the last week which is about 60 pages.

Thanks 
cheers

---

### Post by Moschti on 2009-06-13
Reference to another answer would be also appreciated.

Thanks

---

