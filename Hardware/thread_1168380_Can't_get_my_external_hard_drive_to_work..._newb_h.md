---
title: "Can't get my external hard drive to work... newb help"
date: 2009-05-24
forum: Hardware
---

### Post by AaronMuslim on 2009-05-24
Hey people, I just upgraded to 9.04. Actually, it was a new install. I can't get my external hard drive (usb) to be read properly by the os. I downloaded the gnome-device-manager and it shows the drive listed under the usb controller as the iomega as it is. The hardy version picked it up and mounted it fine everytime. I tried to find it in the fstab file in a newb attempt to mount it to the /mnt dir myself but I could hardly read it. HEH.... I can't access it through natalius (spell check)..... 

Some advice would be lovely 

Thanks people....

---

### Post by benson444 on 2009-05-24
Try mounting it in the terminal. See if it's recognized by the fdisk command, make a directory in /media and then mount it. Replace /dev/xxxx with correct partition listed by fdisk

```
sudo fdisk -l
sudo mkdir /media/iomega_usb
sudo mount /dev/xxxx /media/iomega_usb
```

Any error messages?

---

### Post by AaronMuslim on 2009-05-24
/dev/sda1   *           1       11168    89706928+   7  HPFS/NTFS
/dev/sda2           11169       19457    66581392+   5  Extended
/dev/sda5           11169       19113    63818181   83  Linux
/dev/sda6           19114       19457     2763148+  82  Linux swap / Solaris


... that's the result of fdisk -l 

... I don't see it there I don't think it recognizes it as a disk...

---

### Post by miegiel on 2009-05-24
Is it listed in : ```
lsusb
```

---

### Post by benson444 on 2009-05-25
Or dmesg. Connect it, wait a couple of seconds and run

```
dmesg | tail -n 20
```

---

