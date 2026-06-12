---
title: "Hard Drive Size"
date: 2007-09-29
forum: Hardware &amp; Laptops
---

### Post by monsterfeo on 2007-09-29
Hello there, does anybody know what is the command to find out what the size of my hard drive is?

Thanks in advanced.

---

### Post by ddrichardson on 2007-09-29
df

---

### Post by dabl on 2007-09-29
```
sudo hdparm -I /dev/sda
```

That's a capital letter "eye" to get the details on drive /dev/sda. :guitar:

---

### Post by monsterfeo on 2007-09-29
Thanks guys, but it tells me that there is no sda under dev, I looked at it an I did not find it.

---

### Post by ddrichardson on 2007-09-29
It might not be /dev/sda. Type sudo fdisk -l to get a list of drives

---

### Post by monsterfeo on 2007-09-29
Thanks ddrichardson, it worked very fine. This came out.

Disk /dev/hdc: 61.4 GB, 61471162368 bytes
255 heads, 63 sectors/track, 7473 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        7297    58613121   83  Linux
/dev/hdc2            7298        7473     1413720    5  Extended
/dev/hdc5            7298        7473     1413688+  82  Linux swap / Solaris

---

