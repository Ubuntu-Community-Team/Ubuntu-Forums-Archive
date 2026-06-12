---
title: "Linux version for N2800"
date: 2017-01-29
forum: Hardware
---

### Post by amaidonis on 2017-01-29
Hello!

Can someone tell me which version of Linux (Ubuntu?) is best for using with an Atom N2800 / 2GB DDR3 netbook?


Thanks!
Apostolos

---

### Post by TheFu on 2017-01-29
Lubuntu.  I ran 10.04 Lubuntu on an N2700.  Do not expect hidef video to ever work well. The CPU just cannot keep up and the onboard iGPU don't support either MPEG2 or H.264 video accel in hardware.  My netbook had a 600p screen and I always felt like it was missing 400 pixels (because it was).

Almost any new chromebook would be 2-5x faster than that machine, BTW.

N2800 passmark rating is : [https://www.cpubenchmark.net/cpu.php?cpu=Intel+Atom+N2800+%40+1.86GHz](https://www.cpubenchmark.net/cpu.php?cpu=Intel+Atom+N2800+%40+1.86GHz) - about 620.
A 4 yr old C720 has a Celeron 2955u with a passmark of 1450 [https://www.cpubenchmark.net/cpu.php?cpu=Intel+Celeron+2955U+%40+1.40GHz&id=2073](https://www.cpubenchmark.net/cpu.php?cpu=Intel+Celeron+2955U+%40+1.40GHz&id=2073) - see these on ebay for $50-$85. They can run Ubuntu fine.  Not all Chromebooks are equal and many have really bad CPUs, so do the homework for any other models.

---

### Post by Yellow Pasque on 2017-01-29
Any desktop that doesn't require 3D accel should work well.

---

### Post by amaidonis on 2017-01-29
Thanks guys!

Temüjin - do you have any recommendations for any desktop that doesn't require 3D accel?

Thanks again!

---

### Post by TheFu on 2017-01-29
lxde
xfce
mate

Those are the main,  well-known, options.  Each can be installed outside of installing a new distro, if you like. Howtogeek has a how-to for this. Test them using the guest account first. 

If you need a full distro - Lubuntu, Xubuntu, Ubuntu-Mate ... you get the idea.  Lubuntu would be the lightest. The other two a only slightly heavier for much more "cheese."  Xubuntu is the most complete from a GUI management standpoint, IMHO.  Just depends on what you think a desktop should have.

---

### Post by amaidonis on 2017-02-01
Really grateful!

Thanks! :D

---

