---
title: "30 seconds pause in boot after kernel upgrade"
date: 2009-08-12
forum: Installation &amp; Upgrades
---

### Post by cdysthe on 2009-08-12
Hi,

I followed one of the kernel upgrade guides and compiled a new kernel for my laptop. I had problems with the current kernel and ext4, a problem a 2.6.30 upgrade took care of. 

The new kernel works fine, but I have one problem: Right after I select the new kernel from the Grub menu the disk starts grinding for 30 seconds while there's nothing on the screen. Then I get the normal "Starting up...." message and get a relatively normal boot from there on although I get some text scrolled before the nvidia driver loads that i didn't get with the old kernel.No errors though.

I have looked in the logs and there's no errors anywhere tere either. The only anomaly I can see is that the new kernel has a 47 MB initrd.img while the old one only has a 7 mb one. Could that be what causes the pause, and what could I do to fix it?

//c

---

