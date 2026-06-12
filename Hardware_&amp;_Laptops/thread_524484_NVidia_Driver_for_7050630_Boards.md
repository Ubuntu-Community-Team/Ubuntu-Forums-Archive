---
title: "NVidia Driver for 7050/630 Boards"
date: 2007-08-13
forum: Hardware &amp; Laptops
---

### Post by AchimRS on 2007-08-13
Hi,
I tried the installation of the NVIDIA driver 100.14.11 using the following guideline:
[http://www.albertomilone.com/latest_nvidia_udsf_feisty.html#METHOD_2](http://www.albertomilone.com/latest_nvidia_udsf_feisty.html#METHOD_2)

My board is an ASRock ALiveNF7G-HDready (with the Nvidia 7050/630 single chip) on a normal resolution 1280x1024, but it simply don't work!!!

After reboot it dont start KDE (from KUbuntu Gusty Gibbon Tribe 4), it ends up with the commandline login. If I try to start KDE with "sudo /etc/init.d/kdm restart" it opens a black screen with a blinking cursor top left.

Where can I start searching? Any other ideas how to install??

Currently I use the VESA drivers, without 3D :-(
Achim

---

### Post by AchimRS on 2007-09-07
Aaaarg, so in Gutsy Gibbon this is meanwhile solved, because the nvidia-glx-new package is now from the version 100.14.11.
I was abe to install the driver according the much simpler method:
[http://www.albertomilone.com/latest_nvidia_udsf_feisty.html#METHOD_1](http://www.albertomilone.com/latest_nvidia_udsf_feisty.html#METHOD_1)

Cheers
  Achim

---

