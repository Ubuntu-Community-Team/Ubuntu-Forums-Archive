---
title: "Making a Dual Core &quot;look&quot; like a Quad Core?"
date: 2007-04-29
forum: Hardware &amp; Laptops
---

### Post by laredo7mm on 2007-04-29
How does a program or the kernel know how many cores your computer has?

Is there any way to "mask" the number of cores I actually have and make it look like I have four cores?

TIA

---

### Post by rufius on 2007-04-29
The kernel reads the hardware register off the CPU. That tells it everything it needs to know. In short, there's no way to fool it without doing some serious hacking in the kernel. 

Why would you want to fool the kernel into thinking there's 4 logical cores?

---

