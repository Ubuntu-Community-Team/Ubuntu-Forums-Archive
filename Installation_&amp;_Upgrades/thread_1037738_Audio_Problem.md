---
title: "Audio Problem"
date: 2009-01-12
forum: Installation &amp; Upgrades
---

### Post by vasudev on 2009-01-12
Hi

I have FUJITSU SIEMENS, Amilo M1450 Series laptop.
After installing Ubuntu 7.04 in my system audio is not working....  
Can anybody, please let me know how to rectify this problem.

Thanks in advance
Vasu

---

### Post by damphoud on 2009-01-12
What do you get when you run:
$  lspci |grep Audio

---

### Post by vasudev on 2009-01-12
Hi 

Thanks for the reply
I'll get the the following ouput if i run lspci

$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)

$

---

### Post by vasudev on 2009-01-12
Hi 

audio output through headphone socket is working
only the speakers audio is not working..

thanks

---

### Post by damphoud on 2009-01-12
You probably need update your ALSA version.
What is the output of:
$  cat /proc/asound/version


Check out [http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel](http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel) for your intel chipset. The latest ALSA drivers are 1.0.18a.

---

