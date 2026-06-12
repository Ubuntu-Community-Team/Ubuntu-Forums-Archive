---
title: "How to set the rigth frecuency rate for my monitor?"
date: 2007-10-21
forum: Hardware &amp; Laptops
---

### Post by gato2707 on 2007-10-21
Hi.

Recently I've installed Ubuntu 7.10 in my new computer, every thing is working fine, except the frecuency of my monitor.

The manual of my monitor indicates that it should work at 60 Hz, but Ubuntu only show me the option of 50 Hz.

¿How can I adjust it?

My monitor is a LG Flatron L1718S and the Graphics Card is an nVidia 6150 integrated into an Asus M2N-MX SE motherboard with 2 GB of RAM

Thanks in advance for your help

fpn

Saludos desde México!!!

---

### Post by murius on 2007-10-21
Hi,

I am relatively new to Ubuntu but had the same problem and fixed mine as follows:

I would highly recommend making a backup of the xorg.conf file first!!!


In a terminal window type 
sudo nvidia-settings

This will open up NVIDIA settings, on the left hand side select "X Server Display Configuration"

Adjust settings, then click "Apply",
if all is well then click "Save to X Configuration File", make sure the file is /etc/X11/xorg.conf then click Save.

Quit NVIDIA Settings. 

Hope that helps.

---

