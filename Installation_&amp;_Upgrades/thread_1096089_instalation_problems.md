---
title: "instalation problems"
date: 2009-03-14
forum: Installation &amp; Upgrades
---

### Post by rapshipsarap on 2009-03-14
Hi I'm a fresh ubuntu user but i encountered some problems with the instalation.

It seems that the ubuntu was installed succesfully but when i tried to start it without the cd i got 

error 21 

It is installed on an external disk and on my internal- i have windows xp ,wich would also not start now. 
I tried already typing sudo grub-install /dev/sdb at the command but i get answear:

could not find device for /boot: not found or not a block device

Windows would not start also with or without the usb disk
Can anyone help me ?
Thanks!

---

### Post by zvacet on 2009-03-14
```
sudo fdisk -l
```

Post it here.And for error you can read [this.]("http://users.bigpond.net.au/hermanzone/p15.htm#21")

---

