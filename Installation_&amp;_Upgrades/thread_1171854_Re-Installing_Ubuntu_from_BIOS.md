---
title: "Re-Installing Ubuntu from BIOS"
date: 2009-05-27
forum: Installation &amp; Upgrades
---

### Post by Zebrasectomy on 2009-05-27
I'm in a panic here: I just "tweaked" my girlfriend's laptop and basicly destroyed Ubuntu.
Now, the only way I can re-install it is through the BIOS. 

How do I go about doing this?
To make matters worse, her laptop has no CD drive, and I'm not exactly sure what to do with the ubuntu .iso file thats sitting on my external harddrive (That is what I'm going to use to transfer it over from).

Also, is there any way to recover her lost documents?

Please, please help.

---

### Post by orange-wedge on 2009-05-27
You can use unetbootin to create a bootable image of ubuntu on a usb flash drive using the ISO image.  There are lots of tutorials of how to do this.

As for recovering the documents, most likely the partitions are intact.  Before you do the installation you can mount the partitions while booted on the flash drive and recover any of the needed documents.

Use this to determine the physical location of the partitions:
```
sudo fdisk -l
```For example here is my output:

```
ubuntu@ubuntu:~$ sudo fdisk -l
Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc254c254

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6992    56163208+  83  Linux
/dev/sda2            6993        7296     2441880    5  Extended
/dev/sda5            6993        7296     2441848+  82  Linux swap / Solaris


```Then mount the partition you want to recover:
```
sudo mount /dev/sda1 /mnt/directory
```You may have to create the directory where you want to mount the partition.  The easiest thing to do is to use the same name as the physical, ie /mnt/sda1

Then just copy over the files to an external location.

---

### Post by lindsay7 on 2009-05-27
You should change your post title. I only looked because it makes no sense. You can not install anything from the bios. Bios stands for Basic Input and Output System and is what controls you computer.  Your post should read, "Reinstlling Ubuntu from External Drive".

Anyway, to reinstall Ubuntu, you insert the Ubuntu cd and start the install options. Then you direct it to install on the computers hard drive.

You need to provide for info for anyone to help you more that this. i.e., does it have windows installed, what did you do to break it, does it boot now, and so on.

You can boot from the live Ubuntu cd and look to see if there are any files on the old installation and you could make a directory on you external hard drive and copy them to that and then do your new installation.  It is possible that the old installation is still there but you need to provide more info in order to get more detailed help.

---

