---
title: "compositor - delays in drawing windows"
date: 2008-09-10
forum: General Help
---

### Post by Iliketoplay on 2008-09-10
Hi!

When I turn on the composite manager in my xubuntu, some of the windows I maximize behave strange (not all of them; ie. firefox3 does, gedit not). 
First, the space they would occupy gets black; a milisecond later a part of the image appears, another while later everything is drawn correctly.

My computer is a laptop, r61 lenovo with nvidia quadro 140 card ( [http://www.notebookcheck.net/NVidia-Quadro-NVS-140M.4216.0.html](http://www.notebookcheck.net/NVidia-Quadro-NVS-140M.4216.0.html) ). The RAM I have is 3GB. 
I have installed the nvidia-glx-new package (which according to my knowledge should support my graphic card).

Is my hardware not fast enough for the compositor?
Is there something I've forgotten to configure?

thanks for any help!

---

### Post by overdrank on 2008-09-10
> **Iliketoplay said:**
> Hi!

When I turn on the composite manager in my xubuntu, some of the windows I maximize behave strange (not all of them; ie. firefox3 does, gedit not). 
First, the space they would occupy gets black; a milisecond later a part of the image appears, another while later everything is drawn correctly.

My computer is a laptop, r61 lenovo with nvidia quadro 140 card ( [http://www.notebookcheck.net/NVidia-Quadro-NVS-140M.4216.0.html](http://www.notebookcheck.net/NVidia-Quadro-NVS-140M.4216.0.html) ). The RAM I have is 3GB. 
I have installed the nvidia-glx-new package (which according to my knowledge should support my graphic card).

Is my hardware not fast enough for the compositor?
Is there something I've forgotten to configure?

thanks for any help!

Hi and welcome, the first thing that comes to mind is it being a laptop you may look at the amount of memory being shared with the graphics. this can be adjusted sometimes in the bios. I am not familiar with that model of graphics card so I can not say for sure on which driver is need. If you like you may look at installing the nvidia driver from the site and installing it manually.

---

### Post by Iliketoplay on 2008-09-14
I used EnvyNG, a software that should install the latest drivers ( [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) ) but it didn't help.

I looked into my bios but didn't find any way to configure memory available to the video card. My laptop model is lenovo r61; by the way, here's the simulation of bios for r60: [http://www-307.ibm.com/pc/support/site.wss/MIGR-65602.html](http://www-307.ibm.com/pc/support/site.wss/MIGR-65602.html)

In the XFCE FAQ ([http://wiki.xfce.org/faq](http://wiki.xfce.org/faq)) I've found a notice to add the 
> Option "AccelMethod" "exa"
line to xorg.conf if the graphic card is listed here: [http://www.x.org/wiki/ExaStatus](http://www.x.org/wiki/ExaStatus) . I didn't recognise Nvidia Quadro in any of those abbreviations (so I didn't modify xorg.conf), however I may be wrong.

I'm still searching for a solution...

---

### Post by Iliketoplay on 2008-09-14
...so I typed 'nvidia-settings' and noticed that my gpu uses adaptive clocking. And it doesn't use its full frequency when I enable the compositor. Interesting.

Still searching for a solution...

---

