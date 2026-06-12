---
title: "Can't get Nvidia xorg driver to work again!"
date: 2009-08-18
forum: Hardware
---

### Post by bogoliubov on 2009-08-18
Hello. I just fiddled around to get VDPAU working on Jaunty 64 bit. I installed the 185 driver from the VDPAU PPA, but could not get things to work.

So I wanted to remove all the experimental stuff I've installed. I changed back to the 180 driver, but now the Nvidia graphics driver doesn't work!

In Xorg.0.log I get the following message:
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***

I have the linux-headers-2.6.28-15-generic installed (but not backports) and linux-restricted-modules-2.6.28-15-generic.

So I tried to remove all Nvidia stuff, reboot and the use the Jockey program to install everything correctly. Unfortunately this programs hangs all the time! 

So now I don't know what to do. Please help me get the Nvidia driver working again!

---

### Post by bogoliubov on 2009-08-18
I just noticed that there is no "nvidia" kernel module on my system. And I can't find a way to install it either...?

---

### Post by bogoliubov on 2009-08-19
I even tried to switch back to the 185 version again, but the problem is still there. There must be a way to get the nvidia kernel module back, but I can't find it. Anyone who knows how?

---

### Post by bogoliubov on 2009-08-19
No one? I really need some help here. Can I fix this by running the installation disc and somehow just repair this issue?

---

### Post by bogoliubov on 2009-08-19
Now it's almost working. I found out a little about dkms, and now the nvidia driver is installed.

But I can't get any acceleration, since there's some problem with permissions:
NVIDIA: could not open the device file /dev/nvidiactl (Permission denied).

---

