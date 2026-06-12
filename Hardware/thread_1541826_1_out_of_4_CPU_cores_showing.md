---
title: "1 out of 4 CPU cores showing"
date: 2010-07-29
forum: Hardware
---

### Post by lsutiger on 2010-07-29
This is for my workstation listed in my signature. When I look at cpuinfo, it only shows 1 core. When I look at the system monitor, same there. 
I have a clone machine that shows 4 cores, the only difference it runs 10.04.
I have checked the BIOS settings and it is set to run 4 cores.
No errors during POST. 

Is there a setting in Ubuntu to recognize the other 3 cores? Or has anyone else run across this problem before?

---

### Post by Yellow Pasque on 2010-07-29
You probably need a kernel update to properly handle the Phenom II. [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32/)

---

### Post by lsutiger on 2010-07-29
There was a BIOS update available, so I installed that. Now all 4 show when I boot, but the system becomes unstable using all 4. 

I disabled two cores and I am stable again. Will experiment more with the BIOS tomorrow.

Appreciate the feedback!

---

