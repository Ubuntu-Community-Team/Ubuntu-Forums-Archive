---
title: "Could someone kindly help me? (ATI problem - nearly fixed I think)"
date: 2005-09-12
forum: Hardware &amp; Laptops
---

### Post by [Koba] on 2005-09-12
Hi

Firstly I would like to say how much I love ubuntu after trying various other flavours of Linux. I have just installed a new soundcard which works wonderfully and now I want to get my graphics card (X300 PCI-E) working so I can finally give windows the boot.  :) 

I followed the instructions here ([https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI)) to the letter and after editting /etc/X11/xorg.conf to change "ati" to "fglrx" (step 3 of the Hoary notes) and running fglrxinfo I get this...

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X300 Generic
OpenGL version string: 1.3.4769 (X4.3.0-8.8.25)


As far as I know this is exactly what it should be. So far so good.

I install the doom3 linux demo (which will run on windows) and when I run it I get a blank screen. Same thing happens when I run glxinfo. glxgears works fine though as does fglrx_xgamma.

Here is my /var/log/Xorg.0.log (whole file): 
[http://users.ox.ac.uk/~scat2889/Xorg.0.log](http://users.ox.ac.uk/~scat2889/Xorg.0.log)

I haven't run fglrxconfig as last time I completely messed up my system with it and had to reinstall ubuntu from scratch (mouse,keyboard, everything stopped working)

Any help would be kindly appreciated. Thank you very much.

EDIT: glxinfo works fine now...strange.

[Koba]

---

### Post by Granji on 2005-09-12
I tried that tutorial as well, but to no avail, I found mlomker told me the best way to do it. [Refer to this thread for more detail.](http://www.ubuntuforums.org/showthread.php?t=64286)

---

