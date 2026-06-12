---
title: "Windows to Ubuntu"
date: 2008-08-02
forum: General Help
---

### Post by Dontais on 2008-08-02
I have 2 drives that I typically use for storage with windows, I usally disconnect them format the main drive and use them. Recently I installed ubuntu and cannot acces the files. I was useing windows xp with ntfs is there a way to read these files within ubuntu?

---

### Post by russlar on 2008-08-02
Yup. Ubuntu can read NTFS volumes, you just need to mount them first.

-sudo fdisk -l
this lists all hard drives that your system can see, usually looking like /dev/sdb. Your drive may have a different path, depending on your setup.

-sudo mount /dev/sdb /mnt/your_mountpoint
This mounts the drive /dev/sdb (you should put in whatever comes out of fdisk -l there instead) at /mnt/your_mountpoint (just an example). You'll need to make a mountpoint (directory) wherever you want to mount hte volumes (usually under /mnt).

---

### Post by rEbyTer on 2008-08-02
This is how i get this to work. I'm watching for devices with:
```
$ sudo fdisk -l
```
And i'm going to create a directory under /media folder with
```
$ sudo mkdir /media/ntfs_drive
```
and then i'm going to mount that partition (i'm assuming that is **/dev/sdb1**)
```
$ sudo mount /dev/sdb1 /media/ntfs_drive
```
And from this moment you have your drive mounted and you can view it with nautilus under** /media/ntfs_drive** folder.

If you need to *unmount*, then use this command:
```
$ sudo umount /dev/sdb1
```.

---

### Post by Dontais on 2008-08-04
I tried both your options and when I try to mount it tells me: 


```
user:~$ sudo mount /dev/sda /media/ntfs_drive
mount: you must specify the filesystem type
user:~$ 

```

---

