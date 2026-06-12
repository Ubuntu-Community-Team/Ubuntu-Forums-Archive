---
title: "lid-close event"
date: 2005-06-12
forum: Hardware &amp; Laptops
---

### Post by hagan on 2005-06-12
Hi,
how do I determine the action when I close the lid. In the moment it shuts down the monitor, but I would like it to go in suspend-to-ram. 
The suspend-to-ram is working perfectly, I just have to map it to the lid-close event. Where do I set this.

Thanks
Hagan

---

### Post by kiddo on 2005-06-12
The only thing I could do for mine (closing the lid crashed the laptop) is to comment out everything in some file (sorry, don't remember which one, a bit tired ;)) in /etc/acpi. So I guess you can copy and paste the script from the suspend to ram file

---

### Post by elsewhere on 2005-06-12
The file to check should be /etc/acpi/events/lidbtn, change the script reference from lid.sh to sleep.sh, that should do the trick.

Cheers,
KV

---

### Post by hagan on 2005-06-15
Thats working,

Thanks

---

