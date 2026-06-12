---
title: "How to let Ubuntu 7.10 &amp; 8.04 always mount the same external HD on the same directory"
date: 2008-05-12
forum: Hardware
---

### Post by ICBM on 2008-05-12
Dear all
    I've already known that Ubuntu use UUID to identify & mount HDD in /etc/fstab. Is there any way I can take advantage of this UUID to let Ubuntu system  mount the same external HDD (through USB) on the same folder every time while I plug the external HDD in.
                     Best regard    :popcorn:

---

### Post by hermes0710 on 2008-05-12
Yeap, find out the uuid of the external:
Plug it in and then locate in which device the system mounted it (/dev/?)
Find it's uuid executing this command
```
sudo vol_id -u device
```

where device is the /dev/? entry (ex./dev/sda1). Once you have it, edit your /etc/fstab and add an appropriate entry as you would do before but in the first column instead of "/dev/whatever" enter UUID=theUUID where theUUID is the result of the above command

---

