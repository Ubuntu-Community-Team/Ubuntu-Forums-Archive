---
title: "nVidia Driver Problem (ASUS A8Jm)"
date: 2007-02-06
forum: Hardware &amp; Laptops
---

### Post by nonfiction330 on 2007-02-06
Hi

I am new to linux and I have a problem with my graphic card nvidia driver and some others.

Here's my system spec:
ASUS A8Jm Labtop
Intel Core Duo
nVidia 7600 Go 512mb

Basically what happened was the I tried to install my graphic card driver, using the driver from the nvidia website.  After installation, I used the X server setting provide by nvidia to set my screen resolution to wide screen and save the xorg.conf file after using the x setting for nvidia.  At that point everything is fine.  But after updating ubunut, glx does not work anymore.  I tried on terminal "glxgears" and "glxinf"  all it did is crash and restart x server.

Ok, I tried a different method using guide from ubuntuguide.org.
install using "sudo apt-get install nvidia-glx nvidia-kernel-common"
I had to maually edit xorg.conf to get wide resolution but it works.
After update the glx still works.

BUT for some reason system monitor only show one ( 1 ) cpu where as before driver installation it shows two ( 2 ).  I have a core duo T2300 with 2 core.

Any help would be appreciated.
Thanks

---

