---
title: "[SOLVED] dual boot between windows and 8.04"
date: 2008-05-10
forum: Hardware
---

### Post by bgjmo on 2008-05-10
just wondering if there is anyway to see the NTFS through 8.04.  Was using windows to share my music now i am trying to swap over to ubuntu.  The drive that the music is on is ntfs.  Anyway around this without formatting the drive?

---

### Post by cdtech on 2008-05-11
You'll be able to mount the NTFS drive through Ubuntu. I run a dual boot and mount the windows disc under /mnt/share.

---

### Post by bgjmo on 2008-05-11
> **cdtech said:**
> You'll be able to mount the NTFS drive through Ubuntu. I run a dual boot and mount the windows disc under /mnt/share.

Sorry for the lack of knowledge but how would i go about doing that?

Thanks for the reply

---

### Post by cdtech on 2008-05-11
On the Ubuntu machine type:
```
sudo fdisk -l
```
This will list the drives Ubuntu see's.

Create a directory within the /mnt directory to mount to:
```
sudo mkdir /mnt/share
```
or whatever you want to name it.

Do:
```
sudo pico /etc/fstab
```

This will open the fstab file for editing.

Add a line: (with the disk you see from above that you want to mount, ie: /hdb1 /hda1 /sda1 ect..,and the directory you created above).
```
/dev/hdb1       /mnt/share      ntfs     defaults,locale=en_US.utf8   0    0
```

After all that just:
```
sudo mount -a
```
this will mount the drive. Then anytime you start up your computer it will mount automaticlly.

---

### Post by tazmannusa on 2008-05-11
I mount them from Kubuntu 8.04 from system menu/storage media, If I recall
in Ubuntu  it would be in my computer. just click on drive you want to mount and open. As far as sharing it on your net, I use samba server and it lets me share files from my home folder only. I think there is a way to set it up to share from other places but not sure about sharing from an ntfs drive.
 simplest way would be to put the music you want to share in your home folder  and share from there.
 Tom

---

### Post by bgjmo on 2008-05-12
Thanks thats what i needed to know

---

