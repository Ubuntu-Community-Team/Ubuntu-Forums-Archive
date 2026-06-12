---
title: "Which format"
date: 2006-01-24
forum: Hardware &amp; Laptops
---

### Post by Ubuntuud on 2006-01-24
Hi, I want to format my external harddisk because it is currently NTFS (or NFTS). But there are around ten possibilities and I don't know which one to choose, so I've come for some advice... It isn't necessary that it is cross-platform... Which one should I choose?

---

### Post by MJN on 2006-01-24
If you don't need to allow direct Windows access (i.e. from a multi-boot) then go for ext3.
 
Mathew

---

### Post by Ubuntuud on 2006-01-24
With ext3, will it be possible to read from a windows machine? Or maybe even write?

---

### Post by Adrian on 2006-01-24
[QUOTE=Ubuntuud]With ext3, will it be possible to read from a windows machine? Or maybe even write?[/QUOTE]

You can do both. Just use this driver in Windows:
[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by MJN on 2006-01-24
By 'from a Windows' machine do you mean the machine containing the disk? If so, it looks like Adrian's pointer will do the trick, however if you mean accessing the disk from a Windows machine on the network then for that you'd use Samba [(http://www.samba.org/).]("http://www.samba.org/")
 
Mathew
 
EDIT: Just noticed you said external disk, in which I assume we're just talking about the one machine here? If so, ignore my Samba reference..

---

### Post by Ubuntuud on 2006-01-25
You're right about the external thingey...

---

