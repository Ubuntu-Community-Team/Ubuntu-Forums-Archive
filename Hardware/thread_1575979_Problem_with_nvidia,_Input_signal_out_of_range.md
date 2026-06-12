---
title: "Problem with nvidia, Input signal out of range"
date: 2010-09-16
forum: Hardware
---

### Post by ghostamorx on 2010-09-16
Hey

I installed ubuntu just fine and when I turned on the restricted nvidia driver, after restart I get a message from my monitor that Input signal out of range. And I cant see anything besides the black screen and this white error box. 
I tried many methods by configuring the xorg.conf file. 
Ubuntu has been working on my machine before, but now I get this annoying error after reinstalling it. I can't find a solution.
I have nvidia Geforce 7600GS and my monitor is HP w1907v, with native resolution 1440x900 60Hz
Can anyone suggest anything?

Thanks

---

### Post by ellgor on 2010-09-17
Hi,

You could try this, I read that Nvidid drivers sometimes dont'get loaded in correctly so I found this guide that gets them installed and running:

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
6) When an error message pops up saying that Ubuntu cannot load Nvidia drivers, choose Exit to terminal (Exit to console) or if you get a black screen and nothing works, reboot and as soon as anything appears on screen press the tab key, this will bring up a boot screen where you can go to a terminal.
7) Login and cd to the directory where you saved your file
 Install drivers

sudo sh NVIDIA-Linux-x86_64-195.36.24-pkg2.run (or whichever package you have, be precise as errors will result in "no such file"

Note: When I ran this I got an error message "Unable to find kernel source tree", so I ran:
$ sudo apt-get install linux-headers -`uname -r'

then ran the installer again

8) Follow the onscreen guide from Nvidia and when done
9) Start GDM

sudo service gdm start

Regards, Ellgor.

---

### Post by ghostamorx on 2010-09-17
No that didn't work, still got the Input signal out of range.

Edit: When running failsafe graphics mode, when I Ctrl-Atl-F1, it shows the following error: "Failed to initialize GLX extension (Compatible NVIDIA X driver not found)".

---

