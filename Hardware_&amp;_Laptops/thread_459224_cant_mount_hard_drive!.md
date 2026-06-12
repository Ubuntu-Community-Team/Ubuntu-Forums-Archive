---
title: "cant mount hard drive!"
date: 2007-05-30
forum: Hardware &amp; Laptops
---

### Post by ninjaprawn on 2007-05-30
hi,

i just re-installed ubuntu fiesty, cos i had broken a lot of files, and fixed them, but had caused ubuntu to be clumsy and messy.

got everything working in 1 hour, apart from my second hard drive!

i want to get fstab to auto mount it, but at the minute, the only way i can mount is thru gparted!

terminal mounting wont work, just finding the mount point wont work. 

ive even created the nesecary mount point at /media/HD and entry in /etc/fstab as below

/dev/hda1  /media/HD  /ext3  defaults  1  1

in gparted, /dev/hda1 is where the hard drive is,
                  /media/HD is the mount point
                  ext3 is the driver
and this all mount correctly from gparted!

but i cant mount any other way! what am i doing wrong??????

thanks

---

### Post by taurus on 2007-05-30
Can you post the output of these commands from a terminal?

```
sudo fdisk -l 
cat /etc/fstab
ls -la /media
```

---

### Post by ninjaprawn on 2007-05-30
sorry, i had /ext3 in /etc/fstab instead of ext3 for the driver, that was all it was!

thanks for the reply!

---

