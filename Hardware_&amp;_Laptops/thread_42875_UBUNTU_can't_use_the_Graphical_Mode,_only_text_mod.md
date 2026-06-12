---
title: "UBUNTU can't use the Graphical Mode, only text mode (GLIDE problem, I think)"
date: 2005-06-19
forum: Hardware &amp; Laptops
---

### Post by Cornellius on 2005-06-19
It only gives me a box telling XORG found an error.

I looked at the XORG log and it seems that it's a problem with GLIDE. I have an ASUS GeForce FX 5200 128 Megs. Well, Ubuntu found that it was a GLIDE card (even if it say OPEN-GL on the box of the graphic card), but Ubuntu seems to be unable to find the drivers for it.

What should I do ?

---

### Post by afonic on 2005-06-19
Try running sudo xorgconfig and select the nVidia driver manually.

---

### Post by Cornellius on 2005-06-19
I will... but I don't know the specs like the # of the port where the Card is, etc

---

### Post by afonic on 2005-06-20
You don't need to know any info like that. Run the config. Make sure you select nVidia driver. For any setting you are not sure choose the default.

---

