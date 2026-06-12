---
title: "Cannot boot - initrd.img deleted PLS HELP"
date: 2008-09-17
forum: General Help
---

### Post by cbstryker on 2008-09-17
So here's what happened. I've been trying to get virtualbox to work. It kept giving me an error of some kernel image not being installed. So after playing around for a while with installing various kernel images in the synaptics package manager, I decided to try again from scratch. So I brilliantly selected all the kernel images and marked them all for complete removal (I can feel some of you cringing now).

So this brings me to my problem. Upon reboot I found grub not able to find the kernel. I booted from the live cd and copied the kernel to my /boot directory. Problem is that the initrd.img file is nowhere on the live cd and i've tried a few tutorials to rebuild it with no luck. My boot drops me into a busybox shell.

Can anyone please help!

---

### Post by cbstryker on 2008-09-17
bump?

Anyone have any suggestions?

---

### Post by cbstryker on 2008-09-17
I could really use some help on this one. I've tried everything I could find online to recreate the initrd.img file with no luck. One help site instructs to use "dpkg-reconfigure" to fix it, but in busybox that command isn't found.

---

