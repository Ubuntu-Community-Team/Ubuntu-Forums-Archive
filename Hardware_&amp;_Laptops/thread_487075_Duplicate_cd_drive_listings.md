---
title: "Duplicate cd drive listings"
date: 2007-06-28
forum: Hardware &amp; Laptops
---

### Post by amadeus266 on 2007-06-28
I only have a single cdrom drive installed on this machine but when I open "Computer" it shows that there are 2. Haven't tried using the drive since install because it is very old and the tray sticks alot but it is strange to see 2 entries.

---

### Post by hardyn on 2007-06-28
yeah, that happened to me with .20.16 kernel upgrade.
delete the directory from /media and comment out of fstab.

---

### Post by amadeus266 on 2007-06-28
Whoa!!! I was getting ready to try your suggestion when I noticed that the propeties page for this item shows the following (screenshot). Now I am no Linux Expert by any stretch of the imagination, but it looks like it is my root filesystem!!!


EDIT: If this is in fact my root filesystem, why can't it be mounted?

---

### Post by hardyn on 2007-06-29
you booted, from a hard disk i presume,  so a phantom device cant be your root file system. 
is contains nothing according to the screen shot.

I think you will be fine removing it, you may start my simply commenting it out from the fstab file, and see what happens.

---

### Post by amadeus266 on 2007-07-02
> **hardyn said:**
> you booted, from a hard disk i presume,  so a phantom device cant be your root file system. 
is contains nothing according to the screen shot.

I think you will be fine removing it, you may start my simply commenting it out from the fstab file, and see what happens.

I'll give it a try this afternoon and let you know if ti works. This is my work computer and cannot risk messing it up at the moment.

---

