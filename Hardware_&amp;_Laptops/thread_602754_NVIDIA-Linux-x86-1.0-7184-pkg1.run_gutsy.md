---
title: "NVIDIA-Linux-x86-1.0-7184-pkg1.run gutsy"
date: 2007-11-04
forum: Hardware &amp; Laptops
---

### Post by FEXOR on 2007-11-04
I wanted to build my kernel module manual after MANY tries using the run file or the nvidia-installer on gutsy (which didn't work) and it worked but I don't know how to activate it.

If I really get the GLX to work, I will retest it and post how the NVIDIA-Linux-x86-1.0-7184-pkg1.run package (For me it's the nVidia Riva TNT2 M64 graphic card GLX support needed) is installable for gutsy.

THX for help

---

### Post by dabl on 2007-11-04
Why don't you download and install the Envy script installer?

You want the file:

envy_0.9.8-0ubuntu10_all.deb

Which is halfway down this page:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Download the file, then right-click it and choose "install with Gdebi", and install it.

Then, you can open a console window and enter ```
sudo envy -t
``` to run it in text mode.

:)

---

