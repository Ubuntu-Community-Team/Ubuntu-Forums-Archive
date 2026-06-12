---
title: "Dual processor"
date: 2006-02-03
forum: Hardware &amp; Laptops
---

### Post by eno on 2006-02-03
Hi, I'm a newbie to ubuntu, linux infact.
Just wanted to now how you can check if ubuntu is recognizing both CPU's 
I installed ubuntu on a relative old mobo (BX chipset) with 1GB ram and 2 800Mhz PIII Intel CPU's.
Now I'm wondering if it's running on both CPU's or just one?

---

### Post by rmjokers on 2006-02-03
Try running:

cat /proc/cpuinfo

You should see both CPU's listed if it recognizes them.  If not, you need to install an SMP kernel if you havent done so already.  The default Ubuntu kernel only uses 1 cpu.

The package you need in synaptic is probably:

linux-686-smp

---

### Post by eno on 2006-02-03
Had to install the mps kernel, looks good now thank you!

---

