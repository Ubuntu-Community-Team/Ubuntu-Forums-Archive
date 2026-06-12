---
title: "Hard drive"
date: 2007-12-08
forum: Hardware &amp; Laptops
---

### Post by jhyatt7823 on 2007-12-08
I was transfering some data onto a external hard drive once the data was done transferring I tried to empty the trash and it would not let me.  It said I did not have permission.  So I tried changing owner ship of the files and it said that my hard drive is a read only filing system and I cant do anything to now.  Any one know what the heck is going on and how to fix it?

---

### Post by taurus on 2007-12-08
Applications -> Accessories -> Terminal
```
gksudo nautilus
```
And navigate to where you want to empty your trash can and empty it.

---

