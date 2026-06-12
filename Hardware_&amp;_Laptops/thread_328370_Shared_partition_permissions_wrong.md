---
title: "Shared partition permissions wrong"
date: 2006-12-30
forum: Hardware &amp; Laptops
---

### Post by Talako on 2006-12-30
I used gparted to create an ext3 partition for sharing files between windows and linux, when I go into windows i can write to it no problem, but in linux it tells me that I can't write to it b/c I don't own it, and when I check the permissions, it is owned by root, how do i get in and change it to be owned by all/regular user?
thanks

---

### Post by taurus on 2006-12-30
Where do you mount that partition to?  Let's assuming it's in **/media/share**, open a terminal, Applications -> Accessories -> Terminal, and type

```
sudo chmod -R 777 **/media/share**
```

---

### Post by Talako on 2006-12-30
Yet again saved by the awesome community support of Ubuntu, I must say that it is the best I have yet encountered. Thanks taurus, it fixed it, but im just curious what it all meant, what is chmod? what does the 777 do? BTW, it's mounted as /media/hda3.

---

### Post by taurus on 2006-12-30
Chmod means change file access permission and 777 means everybody can read, write, and execute it, /media/hda3...

---

### Post by Talako on 2006-12-31
Thanks again man:D :mrgreen: 8)

---

