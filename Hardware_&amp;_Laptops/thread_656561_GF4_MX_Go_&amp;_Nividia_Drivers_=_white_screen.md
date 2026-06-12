---
title: "GF4 MX Go &amp; Nividia Drivers = white screen"
date: 2008-01-02
forum: Hardware &amp; Laptops
---

### Post by Rage710 on 2008-01-02
So I installed Ubuntu on my Toshiba 5105-S501 laptop and everything went all good. After playing with the wifi and getting that to work alright, my focus is now to get my video to be accelereated. Upon using a wide variety of options, including envy, gedit to edit my XORG.conf, etc. Whenever I restart my computer after installing the drivers, I am presented with a white screen. I can long in and hear the login sound, its just too bright to see. It almost looks like the screen is over its refresh rate or something. Any ideas?

Also, whenever I try to use the nivida drivers I have to go into an editor and change it back to vesa, and it works perfect.

---

### Post by jazzgossen on 2008-01-03
I have a GeForce 4200 Go, using the nvidia driver (version 96.43.01), and that works well as long as I don't use compiz. Could the white screen be a compiz problem? You could try to add 

Section "Extensions"
Option "Composite" "Disable"
EndSection

to your xorg.conf to forcibly disable compiz.

---

### Post by Rage710 on 2008-01-05
After editing my XORG.conf to add that line (it already had Compiz "enable" and i switched it to "disable") my screen still goes white. :mad:

---

### Post by jazzgossen on 2008-01-07
Which version of the nvidia driver are you using? You could also try to go back to an older version. Other than that, I don't really have any other ideas.

---

### Post by Rage710 on 2008-01-09
How does one go about finding the driver version? And where can I download an older version? 

Thanks!

---

### Post by jazzgossen on 2008-01-10
If you have installed the driver from the repositories, you can do "aptitude show nvidia-glx" or nvidia-glx-new, if that's the one you have installed. That will show the version, among other things.

The easiest way to install another driver version would be to use Envy. Otherwise you can find other drivers at [www.nvidia.com](www.nvidia.com).

---

