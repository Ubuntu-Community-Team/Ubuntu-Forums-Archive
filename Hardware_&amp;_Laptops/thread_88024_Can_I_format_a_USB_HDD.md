---
title: "Can I format a USB HDD ?"
date: 2005-11-09
forum: Hardware &amp; Laptops
---

### Post by Deadl0ck on 2005-11-09
Hi All,
I have attached a USB HDD Caddy with a standard 30GB IDE HDD in it.

It has the NTFS file system on it, but basically I just want it as an extra Linux HDD.

Ubuntu detected it no problem and I can see it fine, but as it's NTFS I can't write to it :(

Is it possible to use Ubuntu to format this drive as a Linux HD (ext3)?

---

### Post by earobinson on 2005-11-09
try using gparted

---

### Post by Deadl0ck on 2005-11-09
Excellent - looks good !!

If I convert to FAT (or ext3 for that matter) will it keep my existing data ?

---

### Post by earobinson on 2005-11-09
if gparted claims that it can convert to fat then to me that suggests that it will do just that convert it (keeping all the data) because if it dident keep the data in my mind that would not be a conversion however you should backup any important data befor you try this

Note "that this is a reverse-engineered NTFS tool, that is, MS refused to give any insight as to how NTFS works, and all of this work is a culmination of guess-and-check efforts."
Original Source: [http://www.ubuntuforums.org/showthread.php?t=87491](http://www.ubuntuforums.org/showthread.php?t=87491) (In this quote they are talking about a diferent partition tool but it applys here also)

---

### Post by Kyral on 2005-11-09
Always assume that when you change a filesystem type, you are going to lose all the data. (ext2 to ext3 is a very special exception)

---

