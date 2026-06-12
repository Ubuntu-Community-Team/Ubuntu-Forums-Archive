---
title: "Can't mount anything"
date: 2006-04-13
forum: Hardware &amp; Laptops
---

### Post by bakie on 2006-04-13
since i have installed the new kernel i cant mount anything.
when i insert a cd in my dvd-rom it doesnt do anything. and when i turn on my external hdd it doesnt mount that either.
any know what i can do about that?

---

### Post by taurus on 2006-04-13
Can you mount them by hand, from a command line or terminal?
```

sudo mkdir /mnt/cdrom
sudo mount -t iso9660 /dev/hdc /mnt/cdrom <-- assuming your CD-ROM is a /dev/hdc

```

---

