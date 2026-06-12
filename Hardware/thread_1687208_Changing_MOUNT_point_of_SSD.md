---
title: "Changing MOUNT point of SSD"
date: 2011-02-13
forum: Hardware
---

### Post by iedgar10 on 2011-02-13
Helllo,

In my hands I have an Asus EEEpc. I'm trying to install Ubuntu 10.04 for my mother on it. This particular model comes with two separate sdds. The first sdd is 4gb and the second one is 16gb. I have read on various posts that the 4gb is faster and is meant to hold the OS.  

In short- 
I installed Ubuntu 10.04 on the 4gb as ext3 to be mounted on "/". 
I formatted the 16gb as ext4 and set it to be mounted on "/usr/local".
I did not know what setting the 16gb to mount on "/usr/local" did until AFTER the installation. 
What I'm trying to do now is change the mount location to something easier to find so that the user (my mother) doesn't have a hard time the files she's going to store. I IDEALLY would like it to be under HOME and call it STORAGE. 

What I have done so far:
[https://help.ubuntu.com/community/MoveMountpointHowto](https://help.ubuntu.com/community/MoveMountpointHowto)
1-went to terminal 
2-gksudo gedit /etc/fstab &
3- changed the location from "/usr/local" to "/home/mary/storage"

THE ISSUE: 
when booting i get an error message, "error mounting /home/mary/storage. To skip press S or M to attempt manual recovery" 

Help? :confused:

---

### Post by iedgar10 on 2011-02-14
anybody? pweaseeeeeee 
i still havent figured it out on my own :(

---

### Post by iedgar10 on 2011-02-21
bump...

---

### Post by deconstrained on 2011-02-21
Does the directory /home/mary/storage exist?

---

### Post by iedgar10 on 2011-02-22
yes, it does. I can find it if i go to "places" and search for it from there.

---

### Post by deconstrained on 2011-02-22
Have you tried mounting it manually? Also, have you tried using the UUID instead of the kernel name (sda4) for identifying the partition in fstab? Running fsck on the device? Adding the AHCI driver to your initramfs (if the SSD is running in AHCI mode)?

---

