---
title: "Nvidia driver, need help!"
date: 2004-11-20
forum: Hardware &amp; Laptops
---

### Post by Psyk[o] on 2004-11-20
Hi,
I've read all the old topics about the nvidia drivers but the problem persist.

I'm running Ubuntu Hoary (with universe and multiverse), then I have xorg installed.
I've tried to install the drivers either throught apt (nvidia-glx) and using the nvidia installer (6629).
When I try to start the x server the screen remain black and I need to rebbot my system manually. I've tried also to add the "NvAGP" "0" option in the device section.

Has anyone have the nvidia driver working under Hoary ?


P.s. Sorry for my poor english :(


CIAO e GRAZIE !

---

### Post by adbak on 2004-11-20
Have you followed the directions for the Binary Driver Howto?  [http://www.ubuntulinux.org/wiki/BinaryDriverHowto](http://www.ubuntulinux.org/wiki/BinaryDriverHowto)

Make sure that you don't deviate from the directions when it gets to ```
dpkg-reconfigure xserver-xfree86
```

Hmm....perhaps you might need to change xserver-xfree86 to xserver-xorg.

Che tu sia fortunato!

A presto.

---

### Post by Psyk[o] on 2004-11-20
Yes, I'm sure that I'm under xorg, the X session work properly with the "nv" drivers. I've tried also with the how-to but I have the same problem, the "nvidia" module was compiled properly and I've loaded the module without any problem. Then when I try to start the Xsession i get a black screen and the system hang :(
It seems to be a common problem but I havent found any solution.

---

