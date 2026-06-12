---
title: "Can't write to SD Card!"
date: 2015-04-22
forum: Hardware
---

### Post by LifeMushroom on 2015-04-22
I plug in an SD Card, and I can't make folders, paste files, or do anything. It's 2GB formatted to FAT, and it always works on Windows, but when I plug it in, I can't write to it on Ubuntu.
I'm using Ubuntu 14.04. Help would be appreciated. :)

---

### Post by coldraven on 2015-04-23
Does it show up in the file manager (Nautius)?
If so, is it mounted? It should show a little black triangle next to it's name. You could right click it and select "mount".

---

### Post by dino99 on 2015-04-23
you did not tell us which card reader it is, so we cant focus on a closer answer
first check that the system detect the plugged card: sudo blkid
[http://askubuntu.com/questions/413171/ubuntu-12-04-2-sd-card-is-not-detected](http://askubuntu.com/questions/413171/ubuntu-12-04-2-sd-card-is-not-detected)

---

### Post by LifeMushroom on 2015-04-23
> **coldraven said:**
> Does it show up in the file manager (Nautius)?
If so, is it mounted? It should show a little black triangle next to it's name. You could right click it and select "mount".
Yes, it's mounted. I can see everything but I can't make files or folders.

> **dino99 said:**
> you did not tell us which card reader it is, so we cant focus on a closer answer
first check that the system detect the plugged card: sudo blkid
[http://askubuntu.com/questions/413171/ubuntu-12-04-2-sd-card-is-not-detected](http://askubuntu.com/questions/413171/ubuntu-12-04-2-sd-card-is-not-detected)
I ran sudo blkid:
saturn@saturn:~$ sudo blkid
/dev/sda1: UUID="a5030753-50d9-4c90-b594-553e12930d72" TYPE="ext4" 
/dev/sda5: UUID="c3bda119-764d-4640-b044-c697c3732025" TYPE="swap" 
/dev/mmcblk0p1: SEC_TYPE="msdos" LABEL="NSMBW" UUID="D316-C905" TYPE="vfat" 
saturn@saturn:~$ 

NSMBW is my SD Card.

---

### Post by LifeMushroom on 2015-04-27
It's a SanDisk 2GB SD Card. Any help?

---

### Post by LifeMushroom on 2015-05-02
Is anyone going to help me or is this thread gonna get pushed back to page 10?

---

