---
title: "Nvidia drivers won't stay put"
date: 2010-08-24
forum: Hardware
---

### Post by Fir3chi3f on 2010-08-24
I originally had the proprietary drivers (256.35) installed for my Nvidia 8800GS, but I changed my motherboard and cpu and realized that I lost my 3D support. (Full desktop effects was disabled)

I had a bunch of trouble but installed the latest drivers in hopes of helping (256.44). It seemed to work after starting gdm, but all was lost again after reboot. As a side note, I had also remove a bunch of the unused video drivers (voodoo and such), but don't recall having this problem after such. 
***
edit: only notable error during installation was a library not being a symbolic link. I thought nothing of it because it was during the installation of 32bit libraries (for compatibility I assume?) -Let me know if I'm wrong
***

What else can I try? Thanks and I'll keep this updated in case I figure it out.

---

### Post by ellgor on 2010-08-25
Hi,

Was having similar problems. found this guide that works:

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

