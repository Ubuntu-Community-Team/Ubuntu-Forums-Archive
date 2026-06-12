---
title: "Q45 and Geforce 8400, blink"
date: 2007-06-30
forum: Hardware &amp; Laptops
---

### Post by BonoLeBonobo on 2007-06-30
Hello !

I've installed Kubuntu on my new Samsung Q45 with a Geforce 8400.
Everything went fine, I finally installed the latest Nvidia drivers from scratch to have my video card work.
So now everythings "works", even 3D acceleration but :

From time to time (about each 30 seconds), my screen blinks (or refresh, I can't see). It is very annoying :/

Do you have any idea to solve this problem,

Thanks *a lot* in advance
Marc

---

### Post by BonoLeBonobo on 2007-06-30
When I disable the glx extension, I have not the blink anymore (but no more glx :/)

---

### Post by WahJam on 2007-08-17
Hello,

I have the same problem with the same laptop, here is a solution. Launch the following command :
gksudo gedit /etc/modprobe.d/options

And add this line at the end of the file :
options nvidia NVreg_RegistryDwords="PerfLevelSrc=0x2222"

That works fine for me.
(Source: [http://www.nvnews.net/vbulletin/showthread.php?t=80888](http://www.nvnews.net/vbulletin/showthread.php?t=80888))

Now, I would like have a working LCD brightness control (Fn+arrow up & Fn+arrow down) :(

-- 
WahJam

---

### Post by damike2k on 2007-09-16
same problem for me

power management doesnt recognize the gamma control...

---

