---
title: "Nvidia GeForce 7600 GT"
date: 2014-12-08
forum: Hardware
---

### Post by irongolem0982 on 2014-12-08
this is probably a really dumb question but... well i have ubuntu and lubuntu installed and i have a nvidia graphics card (GeForce 7600 GT) that i use for gaming. and i assumed that the driver  was installed until i noticed that in system profiler/display/open gl that it says: vendor: unknown renderer:unknown version: unknown direct rendering: no.  now i know (because i transfer this card between a vista pc and this pc) that my card supports opengl 2.1 and direct rendering for a fact. i was told that this is a driver issue. id like to get this fixed... where do i get the driver, and how to install?  please be specific on commands

thanks

Iron

---

### Post by oldfred on 2014-12-08
If you have installed any nVidia drivers from nVidia or PPA, you must be sure to purge that first.

But your model is standard, not old or bleeding edge, so the nVidia driver in the Ubuntu repository will work.

You just need to open System Settings, Software & updates, and then additional drivers tab. 
It will probably show several options and which driver you currently are using. That should be nouveau if no nVidia driver installed.

I usually install the version with -updates at end. 

This should be the same info using terminal:
 # list drivers available, same list as system settings,  software updates,  additional drivers or last tab
ubuntu-drivers devices


 # What is installed
dkms status
      
 lspci -nnk | grep -iA2 vga

 nVidia driver versions:
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)
Legacy drivers by GPU model 
[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)
Updated driver search by nVidia model
[http://www.geforce.com/drivers](http://www.geforce.com/drivers)

---

