---
title: "new 2nd hard drive wont mount"
date: 2007-06-03
forum: Hardware &amp; Laptops
---

### Post by Blond37 on 2007-06-03
so i formatted a second hd in ext 3 and now i cant get it to mount.
doesnt ANYTHING  in ubunto 704 work?
i have yet to do one thing that actually works.

---

### Post by taurus on 2007-06-03
Can you post the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by Blond37 on 2007-06-03
> **taurus said:**
> Can you post the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```


Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4660    37431418+  83  Linux
/dev/hda2            4661        4865     1646662+   5  Extended
/dev/hda5            4661        4865     1646631   82  Linux swap / Solaris

Disk /dev/hdb: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       36481   293033601   83  Linux
tunder@tunder-desktop:~$

---

### Post by jiminycricket on 2007-06-04
What happens (in GNOME at least) if you open Places->Computer, and right click->Properties on the hard drive that you want to mount?  Do you see a volume tab?

---

### Post by vanadium on 2007-06-04
I have done many things in Ubuntu that work, so my mileage varies (I am a full Ubuntu convert since Eastern). Your fdisk -l output suggests that your hard drive is properly formatted. Only, you did not succeed in mounting it. What did you try to mount the drive?

To mount it permanently, you will need to edit /etc/fstab and add a line for your new drive. It is only during installation that Ubuntu automatically recognizes and mounts drives. On a later time, you are in charge as the super boss yourself.

* First, you need to know where you want to mount the drive. I would mount it under the classical /mnt. Create an empty directory there with a name you like for the drive, eg.

sudo mkdir /mnt/my_second_drive

* then edit /etc/fstab. As a safety precaution, first create a backup copy of the original fstab

sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab

Add a line 

/dev/hdb1	/mnt/my_second_drive		ext3	defaults

Save the file.

Type

sudo mount -a

to immediately mount the new drive along (otherwise, you have to reboot)

Don worry: another thing will not work: you won be able to write as a user. If you want to be the only user writing on the disk, then change the ownership of the mount point:

sudo chown Blond37:Blond37 /mnt/my_second_drive

this makes you and your group the owner (make sure you replace Blond37 by your actual user name), and you (alone) will have unlimited access.

A far better (more flexible) approach is to create directories on the drive as a root, then chown these directories to different users. Create a symbolic link of the newly created directory under your own home directory for easy access. Do that for each user.

eg:

cd /mnt/my_second_drive
sudo mkdir Blond37
sudo chown Blond37:Blond37 Blond37
sudo ln Blond37 /home/Blond37/Data

From now on, you will see the Blond37 folder on your second harddrive as the folder "Data" in your home folder.

Instead of the above commands, you can use a sudo nautilus to do that graphically. Yet a superuser Nautilus is a dangerous thing (as dangerous as Explorer in MS Windows), so close it as soon as you have done.

Alt+F2, type gksudo nautilus

Navigate to your second drive, create your new folder there, use right-click to change owner and group, use right-click to Make Link, move the resulting link under your own home directory, rename it to a convenient name (Data in my example).

---

### Post by kag on 2007-07-23
Thanks, I was looking for this very information!

---

### Post by j.miller565 on 2007-07-27
this is great!!! thank you

---

