---
title: "400GB Pendrive"
date: 2009-03-08
forum: Hardware
---

### Post by rajaiskandarshah on 2009-03-08
earlier this morning a friend gave me a 400gb usb pendrive. yup, i know it is a fake. anyway when i inserted it into my ubuntu 8.04, the drive was mounted and displayed 390gb of space available. copied 10gb of my thunderbird email folder and successfully corrupted all other files ;)
anyway i am now using gparted to format it from vfat to ext3 (still displaying 390gb of space). after formating, did a chown and chmod from terminal to give me permission to create and delete files. then created a folder from nautilus. and copied a small file to that folder. then unmount and took out the pendrive.
stuck the pendrive back in and it was automatically mounted. but the folder that i created was not show on nautilus. but from the terminal i can see it but cannot change directory to the folder.

---

### Post by taurus on 2009-03-08
What are permissions and ownership of that directory?

```
ls -la
```
Maybe root owns the mount point, probably /media/disk, so you can't do anything with it until you change the ownership of the mount point again.

---

### Post by rajaiskandarshah on 2009-03-08
this is what i got

ls: cannot access mymusic: No such file or directory
ls: cannot access music_usb: No such file or directory
ls: cannot access my-music: No such file or directory
total 24
drwxrwxrwx 6 iskandar iskandar  4096 2009-03-08 22:28 .
drwxr-xr-x 4 root     root      4096 2009-03-08 23:22 ..
drwxrwxrwx 3 iskandar iskandar 16384 2009-03-08 22:48 lost+found
d????????? ? ?        ?            ?                ? music_usb
d????????? ? ?        ?            ?                ? mymusic
d????????? ? ?        ?            ?                ? my-music

the lost+found folder was automagically created by gparted

sorry, but i am not much of a cli guy - even after 3 years of ubuntu as my main work computer. any help is appreciated.

---

### Post by taurus on 2009-03-08
Try unmount your external drive first.  Then, run a fsck to check for bad blocks.

```
sudo umount /media/**disk**  <-- If that is the mount point.
sudo fsck /dev/**sdb1**  <-- If that's your external drive.
```

---

### Post by rajaiskandarshah on 2009-03-08
hmm... i copied over a 40mb folder on to the pendrive about 10min ago. trying to unmount from the terminal gives me:

umount: /media/disk: device is busy
umount: /media/disk: device is busy

right-click on the device icon on the desktop and selecting unmount volume, unmounts it almost immediately.

running fsck gives me the following:
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
/dev/sdb1 contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Deleted inode 32769 has zero dtime.  Fix<y>? yes

Deleted inode 32785 has zero dtime.  Fix<y>? yes

Deleted inode 32801 has zero dtime.  Fix<y>? 

and these:

fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
/dev/sdb1 contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Deleted inode 32769 has zero dtime.  Fix<y>? yes

Deleted inode 32785 has zero dtime.  Fix<y>? yes

Deleted inode 32801 has zero dtime.  Fix<y>? 

followed by a lot of numbers and finally:

Directories count wrong for group #1836 (2, counted=0).
Fix<y>? yes

Free inodes count wrong for group #3035 (8191, counted=8192).
Fix<y>? yes

Directories count wrong for group #3035 (1, counted=0).
Fix<y>? yes

Free inodes count wrong (25599950, counted=25599966).
Fix<y>? yes


/dev/sdb1: ***** FILE SYSTEM WAS MODIFIED *****
/dev/sdb1: 34/25600000 files (2.9% non-contiguous), 878292/102398302 blocks

---

### Post by taurus on 2009-03-08
Now remount it and see what happens to your files on /dev/sdb1.

```
sudo mkdir /media/sdb1
sudo mount -t ext3 /dev/sdb1 /media/sdb1
ls -la /media/sdb1
```

---

### Post by rajaiskandarshah on 2009-03-08
remounting, i got these:

total 16
16 drwxrwxrwx 3 iskandar iskandar 16384 2009-03-08 22:48 lost+found

root is gone and so are the three 'invisible' folders

the folders i copied are still intact in the lost+found folder

will do a repeat test again tomorrow morning - and see if it is reliable enough. else, it makes a nice shiny paperweight ;p

any other tips that you would recommend ? many thanks

---

### Post by taurus on 2009-03-08
Do a quick test on that external harddrive right now.

```
touch /media/sdb1/testing
ls -la /media/sdb1
```
See a file testing in there?

Don't forget to unmount it first before you unplug it from your machine.

---

### Post by rajaiskandarshah on 2009-03-08
i had unmounted and removed the pendrive before i got your reply. anyway inserting it back and having automount and running the quick test gave me these:

total 24
drwxrwxrwx 3 iskandar iskandar  4096 2009-03-09 00:46 .
drwxr-xr-x 5 root     root      4096 2009-03-09 00:46 ..
drwxrwxrwx 3 iskandar iskandar 16384 2009-03-08 22:48 lost+found
-rw-r--r-- 1 iskandar iskandar     0 2009-03-09 00:46 testing

by the way, just in case you missed it, this is a usb pendrive / thumbdrive ssd device. it was not reliable in windows,so i thought if i could make it reliable enough in ext3, we could see a lot of high capacity ssd on ext3 ;-)

---

### Post by taurus on 2009-03-08
> **rajaiskandarshah said:**
> 
total 24
drwxrwxrwx 3 iskandar iskandar  4096 2009-03-09 00:46 .
drwxr-xr-x 5 root     root      4096 2009-03-09 00:46 ..
drwxrwxrwx 3 iskandar iskandar 16384 2009-03-08 22:48 lost+found
**[COLOR="Blue"]-rw-r--r-- 1 iskandar iskandar[/COLOR]**     0 2009-03-09 00:46 testing


Now you don't see the ???????.

You can remove that file if you want.

```
rm /media/disk/testing
```
Assuming automount uses /media/disk as the mount point for that thumbdrive.

---

### Post by rajaiskandarshah on 2009-03-08
thanks. also testing with a simple copy and paste of a 400kb jpeg file using nautilus. unmount and removed the pendrive. inserted the pendrive and automount and the jpeg file displays ok. will test it out tomorrow with bigger files / folders. many thanks again.

---

