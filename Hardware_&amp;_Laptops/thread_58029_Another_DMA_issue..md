---
title: "Another DMA issue."
date: 2005-08-18
forum: Hardware &amp; Laptops
---

### Post by krusbjorn on 2005-08-18
Hey all.

I have a DVD-rw/CD-RW combo, which I'm trying to enable DMA on. There is no problem turning DMA on, but as soon as I restart the computer, it's back off. I'm on an Athlon64 CPU (but i use the 686 kernel) with an nforce4 chipset.

I have added

 ```
 /dev/hdc {
   dma = on
   }
```

to my hdparm.conf.

I have also added "amd74xx" to my /etc/modules file, and the module seems to be running:

```
lyle@mays:~$ lsmod | grep amd
amd74xx                13980  1
ide_core              129356  4 ide_generic,ide_disk,ide_cd,amd74xx
```

I remember seeing someone with the same problem here on the forums a while back, but i can't seem to find the thread now.

Any ideas?

---

### Post by tseliot on 2005-08-18
If you want to solve your problem once for all (no more problems with hdparm). Try my HOWTO. It's a step-by-step for newbies which will guide you through the compilation of a new kernel (it's also explained how to enable DMA in the kernel). It's very easy, please try it:

[http://www.ubuntuforums.org/showthread.php?t=56835](http://www.ubuntuforums.org/showthread.php?t=56835)

---

### Post by krusbjorn on 2005-08-18
Thanks, tseliot! I'll see if someone comes up with an easier solution, and if not, I'll go compiling. Great guide!

---

