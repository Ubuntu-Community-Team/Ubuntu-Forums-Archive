---
title: "Optimus with Dell Laptop and 13.10"
date: 2013-12-15
forum: Hardware
---

### Post by klaserja on 2013-12-15
Hi, relatively new Ubuntu user here, and after some time of being away from Ububtu, I re-installed it on my laptop (Dell XPS 15z, Core i7, 8GB Ram, nVidia GT540m 2GB video card with Optimus).

I installed 13.10, 6-bit version, only by using 'nomodeset', otherwise, I'd get a black screen before the install would start.
Now, Ubuntu works, but I am stuck at a low resolution (1280x1024) while my laptop screen is capable of 1920x1280.

I have tried installing the Bumblebee drivers using the step-by-step process outlined on many websites, but those have not worked for me. I don't know if I'm doing it incorrectly or not, as I am very much a beginner when it comes to Ubuntu.

If I could get some help with getting this installed correctly, I would greatly appreciate it! If the nVidia graphics card doesn't work, that is fine, I would just like to be able to run Ubuntu with a high resolution. My current OS is Windows 8.1, if that is of any help.

Side note - I was able to get 12.10 LTS to install, but I had to run Ubuntu 2D, and I still had the same problem with the screen resolution. In the past, I had 12.04 installed (I think) and the resolution worked fine, but I do not remember how I got it to work.

Thank you!

---

### Post by oldfred on 2013-12-15
You really need 13.10, but if you install multiple nVidia drivers it gets confused and you have to totally houseclean and start over. 

 Ubuntu on the Precision M3800 or XPS15 Nov 2013
[http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx](http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx)

Were these the instructions you followed.

 Updates to nVidia Prime with 14.04 (only)
[http://www.phoronix.com/scan.php?page=news_item&px=MTU0MDI](http://www.phoronix.com/scan.php?page=news_item&px=MTU0MDI)
Newest nVidia Prime with 13.10 testing may run hot, but option to bumblebee
[http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html](http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html)
[https://wiki.ubuntu.com/X/Config/HybridGraphics](https://wiki.ubuntu.com/X/Config/HybridGraphics)
nVidia Optimus and Ubuntu explained 
[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)
Bumblebee:
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
[http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html](http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html)

---

