---
title: "Installation of NVIDIA Driver"
date: 2007-08-27
forum: Hardware &amp; Laptops
---

### Post by InfoManBR on 2007-08-27
Good Afternoon for All!

         It has some days I installed Ubuntu 7,04 and I adored the system. Already it had used other Linux but none conquered me as the Ubuntu. It possesss fantastic resources and therefore I decided to study the system more the deep one soon to change  total for Linux. This is the first time that I participate of this forum, and I wait to be able to count your aid. 

         Already I searched in fórum, in the Google and in some different places, I tried Restricted Driver Manager, Synaptic, apt-get, Envy and I did not obtain to install driver no way 3D my plate of Video NVidia GeForce 6200 LE (256 MB) with Turbocache in Ubuntu 7.04.

         I tried some procedures indicated here and it does not function. Driver after installed and rebooted the system does not function, and my screen is total black and it does not enter in the X. I ask for that they help to decide this problem me, therefore already I tried of everything and so far I did not obtain to decide and would like to use acceleration 3D in my Ubuntu.

Thanks a lot to that to answer.

---

### Post by Marat Galiev on 2007-08-27
You use this driver?[http://packages.ubuntu.com/feisty/misc/nvidia-glx-new](http://packages.ubuntu.com/feisty/misc/nvidia-glx-new)?
First uninstall you old driver:
sudo dpkg -r nvidia-glx.
when download "new" driver and install it.
sudo dpkg -i nvidia-new....xxx.deb
when sudo nano /etc/X11/xorg.conf,and 
replace string 
driver "nv"
with 
driver "nvidia".
Good Luck!
It works fine with my 7400go.

---

