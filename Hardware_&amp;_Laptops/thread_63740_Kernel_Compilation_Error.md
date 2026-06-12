---
title: "Kernel Compilation Error"
date: 2005-09-08
forum: Hardware &amp; Laptops
---

### Post by vivekian on 2005-09-08
Hi , 

Not sure if this is the right place to be posting this query but will still ask ? Compiled a kernel according to the HOWTO [http://ubuntuforums.org/showthread.php?t=43065](http://ubuntuforums.org/showthread.php?t=43065) . Everything worked fine till i booted the machine from the new kernel and it stopped saying kernel panic. Any solutions or did i do something wrong during compilations coz did not use the --initrd option. 

Thanks in advance,
vivekian

---

### Post by dorris on 2005-09-09
hey, yeah, wrong section...who gives a sh1t

compiling with the --initrd option will help.
If you want to use your existing image, without recompiling, create a new intrd to boot from
```
mkinitrd -o /boot/initrd.img-2.6.12-*YOURKERNELNAME* 2.6.12-*YOURKERNELNAME*
```

---

