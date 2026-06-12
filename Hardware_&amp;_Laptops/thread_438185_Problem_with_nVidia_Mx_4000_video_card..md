---
title: "Problem with nVidia Mx 4000 video card."
date: 2007-05-09
forum: Hardware &amp; Laptops
---

### Post by weapon-x on 2007-05-09
hi ,
I have a AGP nVidia Mx 4000 graphic card .i have installed ubuntu 6.10 on my Pc it works fine,(without card) but when i plug the card in to AGP slot and try to boot up my Pc, My Pc hangs up  during that time.
 
And when i remove it and plug the moniter display in motherboard point Ubuntu boots up normally..

Help me yar to sole this.......:confused:

---

### Post by PILGU on 2007-05-09
I had the same problem with mine. You need to install the Nvidia Driver.

try

sudo apt-get install nvidia-glx nvidia-kernel-common
sudo nvidia-glx-config enable

After that download and installation is completed, run

sudo dpkg-reconfigure xserver-xorg

make sure to chose nvidia in place of nv during the wizard.

it has worked for me.

---

### Post by weapon-x on 2007-05-10
still having same problem.....  **My Card is Geforce 4 Mx 4000**

I tell u my system config..

Intel Corporation 82845G/GL
VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)

and having agp slot .....

---

