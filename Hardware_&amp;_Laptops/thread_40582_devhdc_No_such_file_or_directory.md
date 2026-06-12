---
title: "/dev/hdc: No such file or directory"
date: 2005-06-09
forum: Hardware &amp; Laptops
---

### Post by bonifacio on 2005-06-09
After setting dma on in hdparm.conf

At startup after "Setting disc parameters..."

/dev/hdc: No such file or directory

Why?

Other than that the device seems to work as normal  :-k

---

### Post by DonVla on 2005-06-11
ola,

here's the answer:

[http://www.ubuntuforums.org/showthread.php?t=24046](http://www.ubuntuforums.org/showthread.php?t=24046)

-> then go into your /etc/rcS.d folder and change the startup order of hdparm by setting it to S29:

 
     sudo mv SXXhdparm S29hdparm




greetz

---

### Post by bonifacio on 2005-06-13
Just what I needed.  On top of that I had to copy one to S99 as well, just as described in that thread link it's not late enough.

---

