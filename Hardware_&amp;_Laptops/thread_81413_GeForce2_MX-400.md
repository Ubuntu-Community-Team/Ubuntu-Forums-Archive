---
title: "GeForce2 MX-400"
date: 2005-10-24
forum: Hardware &amp; Laptops
---

### Post by samakv on 2005-10-24
I got to install Hoary on my computer, it has the mainboard Asus A7V and I have the GeForce2 MX-400 (16MB Video RAM) on the AGP slot. My monitor is a Philips 105e, max resolution is 1075x728. Forgot the refresh rate but I think it can handle 75Hz and above.

[http://ubuntuforums.org/showthread.php?t=24205&highlight=geforce2+mx-400](http://ubuntuforums.org/showthread.php?t=24205&highlight=geforce2+mx-400)

I installed nvidia-glx. Installs fine. I run the script nvidia-glx enable. Then rebooted. The PC passed POST, past some of init.d, showed the Nvidia logo but never passed it to go to the GDM login. I think I'm missing something but don't know what.

The main purpose is to get games running especially Cube Engine. Without nvidia-glx, the error message will say something like "Cannot find GLX configuration. SDL execute error, parachute...." to that effect and not exit to the normal gnome terminal prompt (stopped responding). 

What should I do next?

Sam akv

---

### Post by rjwood on 2005-10-24
Do you get a command line? If so I would try

sudo dpkg-reconfigure xserver-xorg

If you don't have a command line  try using ctrl+alt+f1 simultaniously

---

### Post by samakv on 2005-10-25
Thanks. I will try that when I can put time. Have to take my work home. :-)

---

