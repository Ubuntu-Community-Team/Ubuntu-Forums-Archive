---
title: "Writing a Compressed drive image to the drive"
date: 2008-11-08
forum: Hardware
---

### Post by Mr.Macdonald on 2008-11-08
I have a 60 gb drive with partitions galore. I wish to take a image of that drive (/dev/sda) compress it and write it to the drive.

This may seem impossible, but my drive is more that half empty, that means that the compression will be less that half the size of my drive, easily writable to my drive.

I tried:
```

tar -zcf ./sda.img.tar.gz /dev/sda

```

but it didn't work, that or the compression algorithm is so good that it compressed my whole drive at light speed, is their another way to do this (pipes).

My final goal is to super compress this image and write in to a DVD, it seems quite possible to me.

---

### Post by phirestalker on 2008-11-08
if you really mean an image of the drive, meaning that the files in the archive will not be directly accessible without some elaborate piping, then it would be
```
dd if=/dev/sda | gzip > sda.img.gz
```

that should do the trick for ya
oh and to unzip

gunzip sda.img.gz - | dd of=/dev/sda

---

