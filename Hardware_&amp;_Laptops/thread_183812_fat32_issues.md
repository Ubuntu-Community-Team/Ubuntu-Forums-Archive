---
title: "fat32 issues"
date: 2006-05-28
forum: Hardware &amp; Laptops
---

### Post by kb3hkg on 2006-05-28
I have an external hard drive that is fat32 formatted. For some reason it mounts read only, and I can't seem to get it to change that. Even when I try to change permissions it doesn't actually change them.

How can I edit my files?

---

### Post by Sutekh on 2006-05-28
You need to read and follow the instructions in this link

[http://psychocats.net/ubuntu/mountwindows.php](http://psychocats.net/ubuntu/mountwindows.php)

---

### Post by kb3hkg on 2006-05-28
Nope, followed the steps there for fat drive and still read only, any other ideas?

---

### Post by linuchsan on 2006-05-28
How do you mount the drive?

---

### Post by Sutekh on 2006-05-28
Any errors when you try it?  or just permission denied?

Can you post the output from
```
sudo fdisk -l
``` and the contents of the /etc/fstab
```
cat /etc/fstab
``` 
Did you unmount the partition before changing the fstab, then remount?  Settings can only be changed with the partition unmounted.

---

