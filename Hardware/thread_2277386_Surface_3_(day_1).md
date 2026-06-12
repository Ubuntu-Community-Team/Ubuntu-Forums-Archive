---
title: "Surface 3 (day 1)"
date: 2015-05-08
forum: Hardware
---

### Post by gschwind on 2015-05-08
Hello,

This is my experimentation with Surface 3 with 128 Go and Ubuntu 14.04. In term of hardware, the device is fine for me and i did not get bad surprise, but, even if I'm confident that will change, the current support of ubuntu (or linux) is not smooth. Because current support is bad, I did not made a tutorial on how to get it work. Note also I started every thing with an Ubuntu 14.04 Install USBkey, that can boot in efi if you set nomodeset kernel option (I did it manualy).

After a hundred of reboot, I finally achieved the few following things :

1/ I use grub2 as default boot loader in secure-boot mode.
2/ I compiled and set up the kernel 4.0.2
3/ i915 driver does not work currently, I reported the bug -> [https://bugzilla.kernel.org/show_bug.cgi?id=97941](https://bugzilla.kernel.org/show_bug.cgi?id=97941)
4/ thus I use efifb @ native resolution (1920x1080), set by grub2
5/ I made a durty patch to get Surface 3 Type Cover working, bug is also reported: [https://bugzilla.kernel.org/show_bug.cgi?id=97951](https://bugzilla.kernel.org/show_bug.cgi?id=97951)
6/ following instruction for surface pro 3, I get the touchpad working using the Surface 3 Type cover ID
7/ following the same source I get the marvell wifi controler working.
8/ The USB working

The touchscreen currently does not work.

I hope this overview will help people to choose whether or not getting Surface 3. In my side I recomand to wait for a better support.

Best regards

---

### Post by Daniel_Burgarth on 2015-05-19
Great that you got it running a bit at least! Did the pen work?

---

