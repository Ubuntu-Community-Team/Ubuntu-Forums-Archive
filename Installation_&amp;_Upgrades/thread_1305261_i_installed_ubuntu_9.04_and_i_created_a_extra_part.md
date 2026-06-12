---
title: "i installed ubuntu 9.04 and i created a extra partition and can not figure out how..."
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by ORVUEDGK360 on 2009-10-29
i installed ubuntu 9.04 and i created a extra partition and can not figure out how to set it up as a partition for keeping files and data sperate from my main and since i did not set it up like that before installing i cant figure out how to set it up now, please help

---

### Post by bswilson on 2009-10-29
Are you familiar with the Gnome Partition Editor (gparted)?  You can install that tool, which will provide a graphical interface for modifying your extra partition's size, position on disk, etc.

```
sudo apt-get install gparted
```

---

### Post by louieb on 2009-10-29
To make it mount so you can use it when you boot - add it to /etc/fstab.

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=283131") 

If you have questions put the content of **/etc/fstab** and the output of 

```
sudo fdisk -l
``` (lowercase L at the end)

also the output of ```
sudo blkid -c /dev/null

```
in your next post

---

