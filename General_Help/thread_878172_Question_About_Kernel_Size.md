---
title: "Question About Kernel Size"
date: 2008-08-02
forum: General Help
---

### Post by Brando569 on 2008-08-02
Is there really a great speed difference between customizing a new kernel to your architecture (changing the pre-emption, timer, processor arch, etc..) and customizing the kernel to your arch and removing all the stuff that do you dont need in the kernel (video drivers, network drivers, various supports that you will never need, etc...) ?

I always try to do the latter since thats how I learned it but it usually takes me about an hour to go through and disable all the stuff that I dont need, then after I install the kernel and begin using it I find out that I disabled something that I needed. My deb package for the kernel image is usually around 10mb.

Will leaving all this (unneeded) stuff in really effect the speed of the kernel (other than compile time)?

---

### Post by ibuclaw on 2008-08-02
Download and install bootchart:
```
sudo apt-get install bootchart
```
And test it with both kernels yourself :)

Although, tbh. I would expect compiling it to be optimised **with your hardware** would be much quicker than a bloated kernel with a massive load of modules in.

...

This script prints out all modules that you are using. You can look them up in the kernel make-menuconfig list
```
for i in `find /sys/ -name modalias -exec cat {} \; 2>/dev/null`; do /sbin/modprobe --config /dev/null --show-depends $i 2>/dev/null; done | rev | cut -f 1 -d '/' | rev | sort | uniq
```

Regards
Iain

---

### Post by Brando569 on 2008-08-02
sweet thanks

---

### Post by Brando569 on 2008-08-13
it didnt change the boot time at all but the amount of reading and writing did decrease significantly with a smaller kernel

---

### Post by sdennie on 2008-08-13
I think that the idea of a custom compiled kernel increasing boot speed is probably not accurate.  It probably does cause the machine to boot faster but, probably not by an amount a human would notice.  Fiddling with the timer, preemption and processor optimizations may make a difference depending on your workload but, again, it's likely to be so subtle for day to day operations that you wouldn't notice.  Really, I would only recommend using a custom kernel if you need it for hardware support, you want to apply special patches or you simply find it entertaining to do.

---

