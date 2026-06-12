---
title: "Installing Ubuntu Feisty 7.04 with NVIDIA display chipset on laptop"
date: 2007-06-08
forum: Hardware &amp; Laptops
---

### Post by PatBx2 on 2007-06-08
Had a bit of trouble installing NVIDIA drivers for a new Ubuntu Feisty 7.04 installation on a Dell Inspiron laptop.  Laptop has a GeForce4 440 Go chipset.  This solution may be obvious to others, but I'd like to document it anyway.

I didn't care if I had the very latest NVIDIA drivers, just that I had NVIDIA-specific drivers that would enable 3D acceleration.  So I installed the drivers from the Ubuntu repository using:

sudo apt-get install nvidia-glx

The problem was that, once I did that on my Dell laptop, I'd get a blank display when I booted the system.  It took a while to realize that I could still hear the startup sounds--I just couldn't see anything.

Attaching an external monitor showed that the system had fully booted--it was just using the external display port instead of the integrated LCD laptop display.

The easiest way to fix this (since I'm not intimately familiar with the contents of /etc/X11/xorg.conf) was to run the nvidia-settings command, which opens a GUI window for configuring the displays.  The trick with Ubuntu is that you must run the command with sudo, or you won't have the authority to save the /etc/X11/xorg.conf file (and you won't get any message telling you that there was a problem saving the file).

sudo nvidia-settings

It was obvious in the GUI that the laptop LCD display had been disabled and only the external monitor was enabled.  It was also easy to disable the external monitor and enable the laptop LCD display.  I also could have kept both enabled in either TwinView or multi-screen, but I just wanted the laptop LCD display to work.

---

