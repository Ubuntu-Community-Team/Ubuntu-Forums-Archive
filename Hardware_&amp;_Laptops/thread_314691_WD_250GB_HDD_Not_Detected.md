---
title: "WD 250GB HDD Not Detected"
date: 2006-12-07
forum: Hardware &amp; Laptops
---

### Post by confused400 on 2006-12-07
I am new to Ubuntu so I am trying to figure everything out. I have two HDDs a WD 120 and a WD 250. Ubuntu is installed on the 120GB and detects that drive. It doesn't detect my other HDD where all my music and stuff is. Please help!

---

### Post by encompass on 2006-12-07
what is the respons of this command?
```
sudo fdisk -l
```
this will tell if your computer sees the drive.  is it a windows partitions.  for example..  fat 32?

---

### Post by taurus on 2006-12-07
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by confused400 on 2006-12-08
> **encompass said:**
> what is the respons of this command?
```
sudo fdisk -l
```
this will tell if your computer sees the drive.  is it a windows partitions.  for example..  fat 32?

It detects the drive. It is NTFS, not Fat32.



And Taurus, when I follow the steps in the link, something is wrong, so I can't use the steps.

---

