---
title: ":p new in linux world need help installing drivers"
date: 2007-06-16
forum: Hardware &amp; Laptops
---

### Post by nebuntu on 2007-06-16
:D I am completely noob in linux.today i install ubuntu 7.04 fiesty fawn.and i am pretty excited as this is fist time i saw linux on any computer(and thats mine desktop).as a coplete noob i am confused when i try to download drivers for my motherboard and graphics card from nvidia.my configuration is 
AMD athlon 64 3000+
512 ram
nvidia geforce FX 5200LE 128 MB
asus k8n motherboard with nforce 3 chipset
i install 32 bit os.so which drivers i shuld install from nvidia site for my chipset and graphics card.
when i am selecting my graphics card i am getting fallowing options.
Linux x86
Linux x64
Solarisx86/x64
FreeBSD
and when i am selecting chipset then i am getting fallowing option
Linux IA32
Linux amd 64/EM64T
which one shuld i download.
thanx in advance

---

### Post by bone43 on 2007-06-16
have a look at this section..

[http://ubuntuforums.org/showthread.php?t=232059](http://ubuntuforums.org/showthread.php?t=232059)

as for nVidia driver how to there is one of many here..

[http://tuxicity.wordpress.com/2007/04/12/feisty-and-nvidia/](http://tuxicity.wordpress.com/2007/04/12/feisty-and-nvidia/)

:D

---

### Post by logos34 on 2007-06-16
You don't need the nForce chipset drivers--everything is already included in the ubuntu base package.

For graphics, use [**this guide**]("http://www.albertomilone.com/latest_nvidia_udsf_feisty.html").  Try method 1 first using the nvidia-glx-new driver in the Ubuntu repos.  Make sure you've downloaded and installed all the updates FIRST (including new kernel).  

If that doesn't work or you just have to use the latest version nvidia proprietary driver version, you need the 'GeForce FX series' for 'Linux x86' (i.e. NVIDIA-Linux-x86-100.14.09-pkg1)

GOod luck and welcome to Ubuntu!

---

### Post by nebuntu on 2007-06-17
:D thanx logos34 and bone43,
I succesfully install the drivers for graphic card as suggested by the link
**bone43**
> as for nVidia driver how to there is one of many here..

[http://tuxicity.wordpress.com/2007/0...ty-and-nvidia/](http://tuxicity.wordpress.com/2007/0...ty-and-nvidia/)



thanx again it was simple..
**logos34**
> You don't need the nForce chipset drivers--everything is already included in the ubuntu base package.

For graphics, use this guide. Try method 1 first using the nvidia-glx-new driver in the Ubuntu repos. Make sure you've downloaded and installed all the updates FIRST (including new kernel). 

i downloaded all update and my chipset is working perfect now.
and now exploring linux world ..
sorry for late responce

---

