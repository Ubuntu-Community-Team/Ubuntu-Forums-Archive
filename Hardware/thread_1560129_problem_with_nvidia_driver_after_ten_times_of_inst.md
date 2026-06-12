---
title: "problem with nvidia driver after ten times of installation and offline upgrade"
date: 2010-08-24
forum: Hardware
---

### Post by vahidasadi on 2010-08-24
hi everyone
last month i had a fully updated and great installation of lucid and i had installed lots of apps and was happy with that installation but i had to change my hard drive and didn't wanted to lose that installation and since i have limited bandwidth internet connection so i decided to use [this tutorial ]("http://ubuntuforums.org/showthread.php?t=819396") to save my .deb packages.
i installed my new fresh lucid installation and then used ```
sudo dpkg -i *.deb
```
to restore my apps back but after installing and restarting the problem showed itself. i had 3 or 4 kind of nvidia driver packages and all of them being installed and i couldn't log into ubuntu GUI
i tried excluding linux headers, nvidia related packages , nouveau packages , libsvga and .... and did other try with installing driver first then other then other ..................
ten times of installation but non of them worked and i saw lots types of start up screens and read and tested lots of methods
i know a lot of people have problem with nvidia driver especially with lucid but i need urgent help .plz help me
i have attached included and excluded packages list
which one of included files should be excluded too?

---

### Post by ellgor on 2010-08-25
Hi,

Was having issues with Nvidia driver and found this guide that works:

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
8) Follow the onscreen guide from Nvidia and when done
9) Start GDM

sudo service gdm start

Regards, Ellgor.

---

