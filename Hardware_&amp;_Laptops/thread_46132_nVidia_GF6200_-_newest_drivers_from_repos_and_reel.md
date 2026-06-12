---
title: "nVidia GF6200 - newest drivers from repos and reel dark screen"
date: 2005-07-03
forum: Hardware &amp; Laptops
---

### Post by Teo on 2005-07-03
Hi,
my graphic card is GF6200 AGP 64bit - NV44A chip. Exactly this one: [link](http://www.leadtek.com.tw/eng/3d_graphic/overview.asp?pronameid=189&lineid=1&act=1) 

I'm using Ubuntu Starting Guide to install drivers: [http://ubuntuguide.org/#installnvidiadriver](http://ubuntuguide.org/#installnvidiadriver)
After restart, my screen is so dark screen I barely see a thing :/

Drivers are installed correctly, coz with my old GF4MX everything works great - but I don't want to use my old card.

PLS help me, what should I do? - don't know where to start :(

---

### Post by tropotek on 2005-09-05
Did you get any answers to this issue I myself have the same problem with that card.

I have been searching for answers but to no avail.

---

### Post by Teo on 2005-09-05
[QUOTE=tropotek]Did you get any answers to this issue I myself have the same problem with that card.

I have been searching for answers but to no avail.[/QUOTE]
Yup, problem solved.
Use original nVidia drivers from [www.nvidia.com](www.nvidia.com) - I'm using 7667 and everything is AOK.

---

### Post by dysprosium on 2005-09-05
I am having the same problem as well.  The brightness of the screen when using the ubuntu drivers for nvidia (glx) is affected.  I can see a slight outline of what is on the screen if I have the brightness on high.  I have attempted to use the drivers from NVIDIA as described in the ubuntu manual here but this is not working either.  I have all the kernel headers and kernel source but in the end the installation says the kernel was compiled using the wrong source ??  I checked the source with my kernel and it's the same.  Any ideas??

---

### Post by tropotek on 2005-09-05
I have done the same thing as you dysprosium, I hope some one out there can help us. 
My System is:

  AMD Athlon 2000
  ECS KT600-A M-B
  NEW GeForce 6200V+ 256MB (XpertVision)
  Ubuntu Horay

Can any one help here...

What is the trick to getting the nVidia drivers to compile the kernel.
I dont know what I could be missing but it seems as if the nvidia installer cannot
find the src files. I did unzip the archive in /usr/src/linux-source-2.6.10.tar.

Is there environment variable that should be set when trying to install?

---

### Post by tropotek on 2005-09-05
I finaly got it to work.

I installed the correct kernel version headers and the Nvidia compiled the module fine....

---

