---
title: "how to recognise windows partitions ???"
date: 2005-01-17
forum: Installation &amp; Upgrades
---

### Post by ljepava on 2005-01-17
i was using mandrake and suse, and they both recognised windows partitions, but  Ubuntu  doesnt. WHERE can i access windows partitions and HOW,  using ubuntu?  



nOOb

---

### Post by albersag on 2005-01-17
First you have to create a mount directory where you will mount windows partition.

On shell type:

sudo mkdir  /mnt/windowsC 

for example

Later you have to mount fisical (logical better said) partition to this directory.

If hda1 is windows partition:

sudo mount /dev/hda1 /mnt/windowsC

If you want to mount automatically this/these partitions you have to modify fstab.

/etc/fstab 

How modify this, reading the example or searching at google.

Regards

---

### Post by JesseJames on 2005-01-17
how about mounting them?   

for example:
mount /dev/hdXX /your.mount.dir/another.dir -t vfat

hdXX = windows partition (hda1 , hdc1 ... something like that :) )
vfat = is for FAT systems
ntfs = for NTFS ...do NOT write in ntfs partition

---

### Post by ljepava on 2005-01-17
thx

---

