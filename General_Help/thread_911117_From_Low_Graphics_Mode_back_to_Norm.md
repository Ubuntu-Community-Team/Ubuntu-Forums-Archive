---
title: "From Low Graphics Mode back to Norm"
date: 2008-09-05
forum: General Help
---

### Post by CoryMathews on 2008-09-05
I just installed a new nvidia driver so that I could complile opengl on ubuntu. To install the driver I hit ctrl+alt+1 and then typed in 

sudo /etc/init.d/gdm stop
sudo sh NVIDIA-Linux-x86-173.14.12-pkg1.run

Then followed the instructions of the nvidia installer. Then when I boot back up I can only run in low graphics mode. It also installed a, nvidia x server settings app that when I run it tells me 

"You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."

So i run 

sudo nvidia-xconfig
then went back to ctrl+alt+f1 and typed in 
sudo /etc/init.d/gdm restart

and I just went in a big circle. Im still in low graphics mode and cannot get back to normal mode. How can I accomplish this?

Im still somewhat new to linux so please keep that in mind when answering. Thanks.

---

### Post by Ryadt on 2008-09-05
Try ```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by CoryMathews on 2008-09-05
Thanks Ryadt. That solved the small display problem however I still get the same

"You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."

When I try to run the Nvidia Settings. Any Idea why that is?

---

### Post by Ryadt on 2008-09-05
Give envy a shot: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by CoryMathews on 2008-09-05
Hum seems to work. I can compile open gl now. I no longer have the nVidia program, but that doesnt matter. I still get an error when running my program that is saying

"freeglut (./test): Unable to create direct context rendering for window 'A basic OpenGL Window'
This may hurt performance."

But at least it works now. I can figure this out later. Thanks guys.

---

