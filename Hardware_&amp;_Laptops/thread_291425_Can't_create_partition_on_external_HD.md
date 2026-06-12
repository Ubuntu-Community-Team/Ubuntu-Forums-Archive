---
title: "Can't create partition on external HD"
date: 2006-11-02
forum: Hardware &amp; Laptops
---

### Post by aamukahvi on 2006-11-02
Hi,

I'm having an annoying problem with my new Lacie 250GB USB drive. The drive was preformatted as FAT32 and worked fine, but I wanted to preserve the file attributes. Hence I wiped the drive and tried to create an ext3 volume using gparted.

However, I get this error:
```
**mkfs.ext3 /dev/sdb1**
mke2fs 1.39 (29-May-2006)
/dev/sdb1 is mounted; will not make a filesystem here!
```

I have unmounted the drive, deleted all the volumes and reattached the drive, made sure it's not mounted and then tried again to no avail.

Do I have to resort to Windows just to get my drive formatted?

Thanks,
aamukahvi

---

### Post by ReaderRat on 2006-11-02
Try using the LiveCD or [**Gnome PARTition EDitor = gparted**](http://gparted.sourceforge.net/index.php)

---

### Post by aamukahvi on 2006-11-02
Yeah maybe I should try the Live CD. Gparted was the first thing I tried. Thanks anyway :)

---

### Post by aamukahvi on 2006-11-02
Ok, I was able to format it using the shell. A quick ```
mkfs.ext3 -L Lacie /dev/sdb1
```
fixed it.

---

