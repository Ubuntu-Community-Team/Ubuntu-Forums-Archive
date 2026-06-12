---
title: "mkfs.vfat seems to be missing"
date: 2008-10-11
forum: General Help
---

### Post by ATLUbP1 on 2008-10-11
I'm trying to follow the instructions from [http://www.pendrivelinux.com/2008/05/15/usb-ubuntu-804-persistent-install-from-linux/](http://www.pendrivelinux.com/2008/05/15/usb-ubuntu-804-persistent-install-from-linux/)

I come to the point where I need to do:
"mkfs.vfat -F 16 -n ubuntu8 /dev/sdx1"

Here I cannot find mkfs.vfat; however I find "mkfs         mkfs.bfs     mkfs.cramfs  mkfs.ext2    mkfs.ext3    mkfs.minix" listed.

How can I install mkfs.vfat?

Thanks..

---

### Post by bodhi.zazen on 2008-10-11
```
sudo apt-get install dosfstools
```

---

