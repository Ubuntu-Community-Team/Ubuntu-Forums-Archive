---
title: "How to auto mount a drive in 8.04"
date: 2008-07-26
forum: General Help
---

### Post by ogwilson on 2008-07-26
I have a partitian/drive that i want to be mounted on startup. is there an easy way to do this?

---

### Post by drs305 on 2008-07-26
We'll need the following informaton and if you could tell us what kind of partition/drive it is (removable, etc):
```
sudo fdisk -l
sudo blkid
cat /etc/fstab
```

---

### Post by aktiwers on 2008-07-26
You need to add it to your fstab. 

If you post the output of:
```
sudo fdisk -l
```

and tell me the filesystem on the drive, I can help you add it to fstab.

---

### Post by ogwilson on 2008-07-26
> **aktiwers said:**
> You need to add it to your fstab. 

If you post the output of:
```
sudo fdisk -l
```and tell me the filesystem on the drive, I can help you add it to fstab.
File system reads "W95 FAT32"

---

### Post by ogwilson on 2008-07-26
Also, the its a partition on the same drive that the linux install sits on, shared by a swap partition, and a windows NTFS32 partition

---

### Post by drs305 on 2008-07-26
Normally fat32 partitions should mount when you select the partition. However, you can put it in fstab so it automatcally mounts on boot.

Backup and open fstab for editing. If you don't use gedit, substitute your text editor.
```

sudo cp /etc/fstab /etc/fstab.old
gksu gedit /etc/fstab

```

Add this to fstab. Substitute the actual name (sda6, sdb4, etc). Use a mount point that exists or we will create one in the next step (example: /media/myfat32):
```

/dev/**sdaX** **/media/myfat32** vfat users,uid=1000,gid=100,umask=022 0 0 

```

Create the mount point if it doesn't exist. You can use any mount point you wish, including a folder in /mnt, if you prefer. Fat32 creates permissions during mounting but you can make yourself the owner of the folder anyway.
```

sudo mkdir **/media/myfat32**
sudo chown -R *username:* **/media/myfat32**
```

Mount the new partition:
```
	
sudo umount /dev/**sdaX**
sudo mount -a
```

---

### Post by ogwilson on 2008-07-26
Thanks for the prompt reply. I followed those instructions exactly but when i do the command

```
sudo mount -a
```

it says MUSIC-MEDIA doesn't exist, and when i try to open it from the places menu, i encounter this:

```
You are not privileged to mount the volume 'MUSIC-MEDIA'.
```

---

### Post by drs305 on 2008-07-26
If you ran the command:
```
sudo chown -R username: /media/myfat32
```

Did you change 'username' to your username? 

What is the line you put in fstab?
What is the mount point?
MUSIC-MEDIA is the label for the partition you are trying to mount or the mount point?

---

### Post by ogwilson on 2008-07-26
yea. i replaced myfat32 in your prompts w/ the volume's label MUSIC-MEDIA. was that not wise?

---

### Post by ogwilson on 2008-07-26
I changed username to my username indeed. heres the fstab line:

```
/dev/hda3 /media/MUSIC-MEDIA vfat utf8,uid=1000,gid=100,umask=022 0 0
```

---

### Post by drs305 on 2008-07-26
> **ogwilson said:**
> yea. i replaced myfat32 in your prompts w/ the volume's label MUSIC-MEDIA. was that not wise?

It should work. So the fstab should look like:

```
LABEL=MUSIC-MEDIA /media/MEDIA-MUSIC vfat users,uid=1000,gid=100,umask=022 0 0
```

or

```
/dev/**sdaX** /media/MEDIA-MUSIC vfat users,uid=1000,gid=100,umask=022 0 0
```

---

### Post by ogwilson on 2008-07-26
should it literally be sdaX or is that a placeholder for something?

---

### Post by lordadi on 2008-07-26
that's a placeholder for what your MUSIC-MEDIA drive is seen as by ubuntu. for example:/dev/hda1.


Cheers,

Lordadi.

---

### Post by drs305 on 2008-07-26
> **ogwilson said:**
> should it literally be sdaX or is that a placeholder for something?

no, you have to look at the results of 'sudo fdisk -l'. The listing that has the fat32 partition will have a name of /dev/**sdaX** with *sdaX* being the designation of that partition.

For example, when I run 'sudo fdisk -l', here is what my results look like:
```

/dev/**sdc3 **           1161        1245      682762+   b  W95 **FAT32**

```


So for my entry, assuming I've made a mount point of /media/MEDIA-MUSIC
```

/dev/**sdc3** /media/MEDIA-MUSIC vfat users,uid=1000,gid=100,umask=022 0 0

```
**NOTE:** I've gone back and simplified the fstab entry a bit.

---

### Post by xen-uno on 2008-07-26
I'm seeing strange happenings too. If I mount any of the NTFS partitions via Places, auto mount usually (but not always) opens them again on next bootup. Amarok is having trouble every other time because the label is changing ... that is, Window's NTFS S: drive volume label is **Media** (the tracks are located here). Amarok's library is empty the next time around as an additional drive has been created (labeled **Media_**), and the original Media is not accessible (error: Cannot mount volume: you are not privileged to mount the volume 'media'). Does the same thing with the NTFS partition X: (labeled **xen-uno**) and on next reboot is inaccessible, but **xen-uno_** is (created by system, not me). I did not create a mount point dir on the 3 NTFS partitions I hook into, as it seemed unnecessary, but it is, eh? 7.10 had no trouble in this regard, and no mount points were created.

---

### Post by jonian_g on 2008-07-26
GUI application to mount partitions and give write permisions = "Storage device manager"

```
sudo apt-get install pysdm
```

Description in Synaptic:

"Graphical Storage Device Manager
PySDM is a PyGTK Storage Device Manager that allows full customization of hard
disk mountpoints whitout manually access to fstab.
It also allows the creation of udev rules for dynamic configuration of storage
devices"

After installing it go to System>Admin>Storage device manager.

Click the "Assistant" button to set your mount options.

---

### Post by drs305 on 2008-07-26
> **jonian_g said:**
> GUI application to mount partitions and give write permisions = "Storage device manager"

```
sudo apt-get install pysdm
```



If this does for fstab what StartUp-Manager did for menu.lst this will make things a LOT easier for newbies (and the rest of us too).

---

### Post by jonian_g on 2008-07-26
The ubuntu repositories have a lot of wonderful programs. I would recommend to any newbie to go to add/remove and read the description of the programs and their life will be a lot easier.

> If this does for fstab what StartUp-Manager did for menu.lst

Yes it does.

---

