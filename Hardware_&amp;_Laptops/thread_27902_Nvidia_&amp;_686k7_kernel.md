---
title: "Nvidia &amp; 686/k7 kernel"
date: 2005-04-18
forum: Hardware &amp; Laptops
---

### Post by bassMonkey on 2005-04-18
Hi,
I would like to use the 686/k7 kernels but simply installing the ubuntu kernels didn't work becouse the "ubuntu" nvidia module is not suitable for those kernels, am I right?

So I think I need to make a new module for those kernels myself using the nvidia installer. How am I supposed to accomplish this when I don't have the kernel sources?

--confused--

---

### Post by TravisNewman on 2005-04-18
you can always get the kernel sources. Search synaptic for your linux-source and then find your kernel version

But yes, nvidia-glx does work with 686/k7, I'm using it now with no compiling at all :)

I've found that it helps sometimes to install the new kernel, reboot into it, and THEN reinstall nvidia-glx and the restricted modules for the kernel.

---

### Post by bassMonkey on 2005-04-18
[QUOTE=panickedthumb]you can always get the kernel sources. Search synaptic for your linux-source and then find your kernel version

But yes, nvidia-glx does work with 686/k7, I'm using it now with no compiling at all :)

I've found that it helps sometimes to install the new kernel, reboot into it, and THEN reinstall nvidia-glx and the restricted modules for the kernel.[/QUOTE]
 Thanks,
It actually works now... beautiful!

---

### Post by mrtaber on 2005-04-18
I've just switched to Ubuntu from Fedora Core 3, and I'm loving it.  Very very nice.  I too wanted to switch to the 686-smp kernel, but when I did, X would not come up.

Do I need to revert to my original (backup) x conf file, uninstall the nvidia-glx driver (which are attached to the old kernel?), and reinstall?

For a newbie, what would be my order of tasks?

Thanks in advance,
Mark Taber  :)

---

### Post by bassMonkey on 2005-04-18
[QUOTE=mrtaber]I've just switched to Ubuntu from Fedora Core 3, and I'm loving it.  Very very nice.  I too wanted to switch to the 686-smp kernel, but when I did, X would not come up.

Do I need to revert to my original (backup) x conf file, uninstall the nvidia-glx driver (which are attached to the old kernel?), and reinstall?

For a newbie, what would be my order of tasks?

Thanks in advance,
Mark Taber  :)[/QUOTE]
 I did the following:
1. installed the k7 kernel in synaptic
2. changed the Driver "nvidia" line in /etc/X11/xorg.conf file to Driver "nv"
3. reboot to the new kernel
4. install the restricted modules for the kernel (search for restricted)
5. reinstall nvidia-glx
6. change the /etc/X11/xorg.conf back to the way it was before step 3
7. reboot
8. everything worked!    :grin: 

hope this helps...

---

### Post by mrtaber on 2005-04-18
Thanks so much!  I can't wait for work to end so that I can get home to try this!  

Mark :-D

---

### Post by mrtaber on 2005-04-18
OK, got home, jumped right on the computer, and, voila!  It worked like a charm.

Thanks for all the help.

Mark Taber :-D

---

