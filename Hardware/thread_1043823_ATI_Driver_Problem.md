---
title: "ATI Driver Problem"
date: 2009-01-18
forum: Hardware
---

### Post by rhcodey on 2009-01-18
I'm a complete newbie  who just installed Ubuntu 8.10. My graphics card driver is ATI radeon Mobility MLP 6Y, I believe. When I install Ubuntu the screen resolution is fine and the graphics are fine as well. But then when I try to install the ATI Control Catalyst (in the hopes of being able to use Compiz-Fusion to create 3D effects and AVN for a dock), I get a low graphics message and my screen resolution goes from 1400 to 800X600.

I've checked the hardware drivers and nothing lists there. My question is how can I get my graphics back to the point at which they were before. I've done research on the issue and attempted several fixes I've found on Ubuntu forums (running aticonfig, etc.), but nothing works. Any assistance you could provide would be much appreciated.

Thank you.

---

### Post by mobasher_helmy on 2009-01-25
Hi, 
Well, i donno if my solution would be of much help to you or not, since i have ubuntu 8.04. and i have ati x1400 mobility radeon grafix card.

I had the same problem of resolution and direct rendering switched off (simply, driver is not functioning). And i did the following:

1- download the driver file from ati.amd.com (select the appropriate model from the selection list)

2- the file is probably a shell script (*.sh) so you have make it executable. chmod +x ati_driver_filename.sh 

3- uninstall other graphics drivers that ubuntu installs by default for your convinience. Theses include the following packages: 
  xserver-xgl (probably used for the fancy desktop effects)
  xserver-xorg-video-ati
  xserver-xorg-video-all

if you don't know how to remove them, u can either use the synaptic package manager (GUI) or use the command line apt-get remove <package_name> as super user of course

4- reboot your machine
5- when you come back you will probably either have a console login, or ubuntu will automatically load the default vga driver which is a basic driver with small resolution support (800x600 is the most probable output)

6- if you would like to use the GUI, fine, just login. Or you can login to the cli with the alt+ctrl+f1 that will bring you to the first console.

7- login with whatever, then open a terminal (in case GUI) and switch user to superuser (simply type su or su -) 

8- navigate to where you downloaded your ati driver. Then execute it.
for example: 
root@my_linux_machine# ./ati_driver_version.sh 

9- follow the instructions (simple ones, just agree to the licence)
10- after the installation finishes, use the aticonfig tool like the following:

root@my_linux_machine# aticonfig --initial --input=/etc/X11/xorg.conf
root@my_linux_machine# aticonfig --resolution=0,1440x900

use your desired resolution of course.

11- reboot or alt+ctrl+backspace

12- i hope you would say: Voila ! 

I installed the driver for the first time after ubuntu installation and everything was fine, but then after i downloaded some updates (a new kernel) everything went crazy and i had to remove all the graphics drivers as illustrated then install my proprietary driver manually.

Thank you,
Mobashsher.

---

### Post by jocko on 2009-01-25
> **rhcodey said:**
> My graphics card driver is ATI radeon Mobility MLP 6Y, I believe.
First of all, check which graphics card you actually have. I can't find any information about any "MLP 6Y". Post the output you get from running this in a terminal:
 ```
lspci | grep VGA
```

---

