---
title: "Dell Inspiron 9400 w/ External Monitor"
date: 2008-05-18
forum: Hardware
---

### Post by dan_s28 on 2008-05-18
Issue: External Dell Flat Screen Monitor will not work with laptop.

Details: Ubuntu 8.04. The External Flat Screen will come on before X starts. I can toggle the screen with Function Key + CRT/LPS.
Once X starts then it switches back to the Laptop display.
xrand does not display that the VGA output(flat screen) monitor is connected.

The external flat screen has two different cable options, DVi and VGA - I have tried them both.

I think it is improper xorg.conf setup. I just don't have the extra option to enable video output? 

Or my laptop video card drivers don't support it on this model?
The video card chipset is NVidia GeForce GO 7900 GS.

I am using the "restricted" driver installed by the restricted driver tool in Ubuntu.

I have found threads on various ways to run dual monitors or extend my desktop, but that is not what I want to do. That does not solve my problem. You would think just connected an external monitor would be simpler!

I can post my xorg, but it really has nothing in it - only thing is it is using the "nv" driver. Hardly any extra options - it is just the default ubuntu generated file. I have not modified it yet.

Thanks,
Dan

---

### Post by dan_s28 on 2008-05-19
This did it. I added these lines to xorg.conf under the Device section which specifies the video card driver.
---------------------------------------------- 
Option "TwinView" "True"
Option "TwinViewOrientation" "RightOf"   
Option "UseEdidFreqs" "True"
Option "MetaModes" "1280x1024,1280x1024; 1024x768,1024x768"
Option "UseDisplayDevice" "CRT"
----------------------------------------------
also note: Option "UseDisplayDevice" "string" #replace 'string' with either 'DFP' (Digital flat panel connected via DVI port), 'CRT' (any monitor that is connected via VGA ports), or 'TV'

---

