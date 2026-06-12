---
title: "Dual Core Problems"
date: 2008-02-21
forum: Hardware &amp; Laptops
---

### Post by junkam on 2008-02-21
I have two problems. 

My Ubuntu only identify a single core (out of two). 
Looking at the forum previous posts I tried to reboot into the generic kernel and yes, ubuntu display both cores. 
However in the generic kernel it does not recognize my display and switches me to a low resolution. Trying to change the xorg.conf does not help, it goes back to the lower resolution. 
In the "non generic" kernel it works fine with the display driver (Nvidia) and I have good resolution but only one CPU core.

I'm lost, please help

---

### Post by patrickfromspain on 2008-02-21
sudo apt-get install linux-generic and lets see if it works. If you are using the ubuntu supplied nvidia driver, this should take care.

If you installed the nvidia driver through envy or manually, you will to do that again from the generic kernel.

---

### Post by junkam on 2008-02-21
I'm getting
linux-generic is already the newest version.

EDIT: - Thank you I managed to fix it by reinstalling the NVidia driver via Envy

---

### Post by coolclassic on 2008-02-21
This may not be relevant but having just replaced a single core processor to a dual core I have found that using the same kernal both kde3 and kde4 respond differently.
Kde3 does not use dual core
Kde4 does use dual core

Various system monitors were used to measure cpu performance.

---

