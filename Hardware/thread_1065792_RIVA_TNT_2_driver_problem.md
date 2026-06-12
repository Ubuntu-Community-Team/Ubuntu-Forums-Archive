---
title: "RIVA TNT 2 driver problem"
date: 2009-02-10
forum: Hardware
---

### Post by eddieu on 2009-02-10
Hello,

I'm new in this and I've installed ubuntu 8.10 desktop edition on my old p.c. to learn more about it.

And the problems started to appear. I have an Intel Pentium III Processor (@ 1000MHz) 512 SDRAM, 160 GB Maxtor HDD and...a NVIDIA RIVA TNT2 @32MBRAM Graphinc Card witch I can't install.

I tried to install it directly (as windows user) with double click on 
"NVIDIA-Linux-x86-71.86.06-pkg1.run" but it says: 

"Could not open the file /home/eddie/Desktop/NVID…nux-x86-71.86.06-pkg1.run.

gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again."

I've searched ubuntuforums.org and I've tried the console version of install:

"what i do is remove ALL nvidia packages in synaptic.. purge.
anything with the name nvidia in it.

then download the nvidia driver from nvidia's site. (or do this first..whatever..)

then CTRL-ALT-F1, login..

sudo /etc/init.d/gdm stop (need to stop the graphic interface)

sudo -i (to get a root shell, u can destroy your system in here with the wrong command, be careful, you have root access in here.)

navigate to the directory where the NVIDIA-Linux-x86-177.82-pkg1.run downloaded file is.
if for example you downloaded the file to your Desktop then it would be:
cd ~/Desktop
or
cd /home/yourusername/Desktop

then type:
sh NVIDIA-Linux-x86-177.82-pkg1.run

go through the install, let it compile a kernel module if it needs to, and answer Y when it asks if it can modify your X configuration file(xorg.conf).
(it may tell you you need to install kernel-headers or something else like gcc, binutils, follow the instructions and use 'apt-get install <pkg>' to install what it tells you you need.)

when the install is complete, exit the root shell
type: exit

then restart the graphic interface
sudo /etc/init.d/gdm start"

It didn't work either. I receive the following error message: Unable to build the Nvidia Kernel module.

Reading other forums I found that RIVA TNT 2 it's a little bit tricky on Linux. Smth like 3d is not working...I don't want to play games on linux. I just want to see how it works and what can it do with network, security over network and web proxy (for start), and I really want to see in full screen resolution mode (as in 1280/1024 or 1024/768, not 800/600).

Can anyone help me?

Thank You,
Eddie

---

