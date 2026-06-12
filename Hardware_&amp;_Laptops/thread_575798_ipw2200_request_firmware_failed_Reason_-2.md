---
title: "ipw2200 request_firmware failed: Reason -2"
date: 2007-10-14
forum: Hardware &amp; Laptops
---

### Post by peertje on 2007-10-14
Hi!

I've tried to compile I working kernel a few times and finally it boots up, but now my wireless doesn't work...dmesg told me that the firmware could not be loaded, but it is in my lib/firmware/2.6.22.6.
Kernel version: 2.6.23

Cheerz!

---

### Post by anubhavrocks on 2007-10-14
Shouldn't the firmware be in 
```
lib/firmware/2.6.23
```

---

### Post by peertje on 2007-10-14
Indeed, stupid that the folder didn't excist :S ...
I allready tried to rename it to 2.6.23.5 (I've compiled it as revision 5) but that didn't work.

Tnx! :D

---

### Post by mojozoox on 2007-10-18
Did this work? That is, creating a new directory say /lib/firmware/2.6.23.5, and moving your firmware files there. Did that work. It did not work for me.

---

### Post by mhubs on 2007-10-18
I just make a symbolic link from the current firmware dir to one named after the kernel i made

---

