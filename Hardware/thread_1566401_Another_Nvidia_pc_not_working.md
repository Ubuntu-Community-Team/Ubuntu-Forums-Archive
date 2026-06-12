---
title: "Another Nvidia pc not working"
date: 2010-09-02
forum: Hardware
---

### Post by Ghost_Mazal on 2010-09-02
Lo guys ,

I have searched but can't find a real solution for this problem.
I get the black screen (screen goes into suspended mode) after installing the Nvidia drivers.

I installed the (current recommended) drivers via the hardware drivers section.
Reboot , after splash screen the monitor shuts down.
I had to boot in recovery mode and remove the driver to get working again.
I can't find a real sollution through my searching.

My card is a Geforce 9800 GT 512mb PCIE, 2 DVI ports , no VGA ports. It connects from DVI to a 19" LG Studioworks CRT monitor. (DVI to VGA dongle connected in the card's DVI port and screen connects into the dongle)

This was an unresolved issue 3 years back when I was last with Ubuntu and dissapointed to see it still as is on my return.

Is there a way to get it working that I can try please ?

---

### Post by ellgor on 2010-09-02
Hi,

I found this guide that works, hope it works for you:

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

