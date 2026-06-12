---
title: "Graphics issues (modesetting??) using maverick and natty with mobility radeon hd 4650"
date: 2011-03-05
forum: Hardware
---

### Post by PaulJ1 on 2011-03-05
I have been trying to get ubuntu 10.10 to work on my laptop.
When I install this version it will boot and get to the login screen.
When I login in all that shows is the last thing on the screen and a pointer (at least that part works). Switching between at virtual terminal and back to Xorg the text remains and the pointer shows up again, but still no graphical desktop. 
When I log into the graphical desktop, using the safe mode (ubuntu has put one in the login screen) the desktop will appear but desktopeffects will be turned off. Running glxgears will not work, so some 3d problems?? Taking some hints from googling around, I found that booting with radeon.modeset=0 will help getting into the desktop, but uglyfies the startup screen (lower resolution).

Trying to run ubuntu 11.04 (one of the alpha versions) as a live-desktop showed similar behaviour. Also with mint 10 (which is based on ubuntu 10.10) I experienced the same graphics-mode behaviour. I was able to ru
n kubuntu 10.10 but noticed that desktop effects were turned off.

Everything works perfectly in ubuntu 10.04 (the LTS version). Did something change so drasticaly that my graphics card (unfortunately integrated into the laptop motherboard) is no longer supported??

Can anyone point me to some information or instructions that will enable me to work around these issues?

---

### Post by fjgaude on 2011-03-05
Well, going from 10.04 to 10.10, xorg.conf seems to be dropped. The graphic video driver seems to be in the kernels now. So what you need is the name of your video chip and google that. From there someone likely has a way to proceed.

---

