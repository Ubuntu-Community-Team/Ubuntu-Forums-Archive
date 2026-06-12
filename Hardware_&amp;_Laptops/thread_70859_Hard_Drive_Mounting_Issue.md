---
title: "Hard Drive Mounting Issue"
date: 2005-10-01
forum: Hardware &amp; Laptops
---

### Post by DariusTriplet on 2005-10-01
I have a second hard drive, and want to mount it to my filesystem.  I'm 99% sure that it's labeled in /dev/ as "hdd," but whenever I try and run "sudo mount /dev/hdd /mnt/" I get the following error:
mount: hdd already mounted or /mnt/ busy
Any ideas as to why it refuses to let me mount the drive?
(EDIT)
Nevermind, I think I got it (needed to mount hdd1)

---

### Post by fabiand on 2005-10-06
Hey,

you should mount any hd to /mnt.
Create a folder inside /mnt and mount the appropriate device on it..

like:
```

mkdir /mnt/my_dev_hdd
mount /dev/hdd /mnt/my_dev_hdd

```

Oh: Unmount the device before mounting it somwhere else ...

- fabiand

---

### Post by Vulpus on 2005-10-06
[QUOTE=fabiand]Hey,

you should mount any hd to /mnt.
Create a folder inside /mnt and mount the appropriate device on it..

like:
```

mkdir /mnt/my_dev_hdd
mount /dev/hdd /mnt/my_dev_hdd

```

Oh: Unmount the device before mounting it somwhere else ...

- fabiand[/QUOTE]

It is actually better to mount hard drives to /media as I discovered recently.  For some reason /media is treated slightly different from other folders.  

They will work when mounted as /mnt though as i used to do that before I was shown the error of my ways.

---

