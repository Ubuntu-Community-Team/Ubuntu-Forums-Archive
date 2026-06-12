---
title: "Splended Ubuntu Hoary 5.04 3D Acceleration Radion 9800"
date: 2005-07-21
forum: Hardware &amp; Laptops
---

### Post by grimdestripador on 2005-07-21
As a result of me constantly reorganizing my hardrives, this will be the 3rd i'm i've been lost on the internet figuring how to get some sweet action acceleration. I prefer 3d games so the default MESA Open GL drivers just won't cut it. But i can't find instructions anywhere that list it on Google. I hope this works well for others. Well hopfully I'll help some ubuntu n00b show off the unreal touney 2004 on linux.
I also suggest that you post how you got your video cards in top performace from a fresh install of hoary.

The ubuntu site seems to recomend some version that uses MESA as the renderer.

This version uses ati's own driver. (glxgears @ 3893 FPS on Radeon 9800)

#***Start of pSUDOcode***  Radeon 9800 LE fglrx Ubuntu Hoary 5.04 ***********
#'goto ati's website and download the lattest bin and rpm files.
sudo pico /etc/apt/souces.list
#-Remove pound sign Before Repositories
sudo apt-get update
sudo apt-get install build-essential
sudo apt-get install linux-headers-686
sudo apt-get install linux-headers-386
sudo apt-get install linux-headers-2.6.10-5
cd <directory where rpm file is>
sudo alien fglrx_6_8_0-8.14.13-1.i386.rpm 
sudo cp /usr/X11R6/lib/libGL.so.1.2 /usr/X11R6/lib/libGLso.1.2.backup
sudo rm /usr/X11R6/lib/libGL.so.1.2
sudo dpkg -i --force-overwrite fglrx-6-8-0_8.14.13-2_i386.deb
sudo mv /lib/modules/2.6.10-5-386/kernel/drivers/video/fglrx.ko $HOME
cd /lib/modules/fglrx/build_mod 
sudo chmod 777 make.sh
sudo ./make.sh
cd ..
sudo chmod 777 make_install.sh
sudo ./make_install.sh
sudo dpkg-divert --package fglrx --add /usr/X11R6/lib/libGL.so.1.2
sudo cp /etc/X11/xorg.conf /etc/X11/worg.conf.backup
sudo fglrxconfig
cd <directory where run file is>
sudo bash ati-driver-installer*.run
#*******end*********

---

