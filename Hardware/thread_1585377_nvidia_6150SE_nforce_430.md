---
title: "nvidia 6150SE nforce 430"
date: 2010-09-30
forum: Hardware
---

### Post by phsilver on 2010-09-30
I wander why I can´t enable compiz fusion full effects!!!
I tryed all existing drivers, but there is no way to enable them...

Does anybody can do that?

Is there something can do manually instead of the authomatic instalation by Synaptics???

I´m trying to do this in Linux Mint distribution, tha last one.

Thanx in advance!

---

### Post by ellgor on 2010-10-01
Hi,

I found this guide that gets the latest drivers in and running:

1) Download Newest Nvidia drivers from their website
2) Open module blacklist as admin:

sudo gedit /etc/modprobe.d/blacklist.conf
3) Add these lines and save: 

blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv
4) Uninstall any previously installed Nvidia drivers: 

sudo apt-get --purge remove nvidia-*
5) Reboot your computer
6) When an error message pops up saying that Ubuntu cannot load Nvidia drivers, choose Exit to terminal (Exit to console)
7) Login and cd to the directory where you saved your file
 Install drivers

sudo sh NVIDIA-Linux-x86_64-195.36.24-pkg2.run (or whichever package you have, be precise as errors will result in "no such file"

Note: If you get an error message like this "Unable to find kernel source tree", do this:
$ sudo apt-get install linux-headers -`uname -r'

then ran the installer again

8) Follow the onscreen guide from Nvidia and when done
9) Start GDM

sudo service gdm start

Ignore my stats I'm on mint 9 now

Regards, Ellgor.

---

### Post by phsilver on 2010-10-01
Thanx for your answer... but

**1)** when I put this: sudo apt-get --purge remove nvidia-*

an error occurs telling me there is nothing to remove

**2)** this: 
6) When an error message pops up saying that Ubuntu cannot load Nvidia  drivers, choose Exit to terminal (Exit to console)
7) Login and cd to the directory where you saved your file
 Install drivers

never happens after rebooting

**3)** Doing this:  sudo sh NVIDIA-Linux-x86_64-195.36.24-pkg2.run

the installation aborts because the Nouveau driver is still installed. I try to uninstall using package manager... but the same.

Other funny thing: Obviously I can connect to Internet and upgrade packages... but in the staus bar of the Update Manager tells me: "Can't connect to Internet"

WHaaaatttt ???? I`m actually surfing the web !!!!!

Any Idea!

I am trying to install Linux Mint 9 Isadora.

Regards!

---

### Post by phsilver on 2010-10-01
Hi again...

I finally could enable compiz effects... the solution???

wel, In package manager I selected ALL nvidia drivers, and in Restricted Hardware, I chose a driver with the number 173 between brackets

Tasks to do: uninstall all packages that has nothing to do with the selected one...

But I still have the problem with Update Manager: Can't connect to internet... so: I can't update my Linux !!!!!
damn!

Regards

---

