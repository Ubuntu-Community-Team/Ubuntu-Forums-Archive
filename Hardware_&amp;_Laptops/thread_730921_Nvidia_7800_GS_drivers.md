---
title: "Nvidia 7800 GS drivers"
date: 2008-03-21
forum: Hardware &amp; Laptops
---

### Post by Cl0ud_nyn3 on 2008-03-21
Wel yesterday I installed Ubuntu and had no problems, except for my Geforce 7800GS, I downloaded the drivers from thier website, logged into root, and attemped to install the drivers, when i did so i was prompted with "you appear to be running an X server Please shutdown and restart installation"

so i attempted to shut down X server, when that happens the screen goes blank and sends me to the login screen, so I attempt to change the run level by going to CTRL+ALT+F1 and typing telinit 3, returned to the gui and then attemped again, and didn't work, so now i have no idea what to do.

---

### Post by jimv on 2008-03-21
Reboot.

Go to Settings > Adminstration > Restricted Drivers

Check where it says to use the restricted Nvidia driver

Reboot again

Enjoy

---

### Post by Cl0ud_nyn3 on 2008-03-21
I've that as well, but when i start, a check screen comes up and wont go away until I hit enter, then it says its in low graphics mode, and i can't go higher than 800x600, when i set the native resolution of my LCD screen which is 1680x1050, it only lets me go as high as 1400x1024, maybe theres something missing here, with windows, i have to install a driver for the monitor, but they only offer an Exe file and no unix support :-/

---

### Post by Mihai Chezan on 2008-03-21
It could be because nvidia-glx is installed instead of "nvidia-glx-new" package.
Try installing "nvidia-glx-new" package from synaptic or command line then reboot.
If still doesn't work run also nvidia-xconfig (as root) then restart x.

---

### Post by Cl0ud_nyn3 on 2008-03-21
Could you tell me how to run Xconfig, all i see is a folder with alot of C source files, and thats it :-/

sorry I'm really new to Ubuntu

---

### Post by Cl0ud_nyn3 on 2008-03-21
Ah, I've fixed the problem, I had to install the unix driver for my monitor to use it properly, that was a real pain but now its done, i appreaciate the help because I wouldn't have made it that far without it, but I have one more question I'd like to ask and I've already googled it, but how do you install a sondcard?

because the OS isn't auto detecting it :-/

its a Creative X-fi Extreme Gamer

Thnx

---

