---
title: "Can't run nvidia-settings"
date: 2008-08-04
forum: General Help
---

### Post by theolster on 2008-08-04
Hi - I've recently installed a new graphics card MSI GeForce NX7300, and the screen colours look very weird.  I have fiddled with my monitor as best I can but believe the problem would be best fixed by running nvidia-settings and adjusting the brightness/contrast/gamma.

However, when I do I get this error: ```
You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 
```Running nvidia-xconfig and a reboot does not fix this error.

I have tried using envy to install drivers, nvidia-glx-new and have currently settled on nvidia-glx.  Note all three drivers provide me with excellent 3d graphics and compiz looks great I just can't run nvidia-settings.

I really need to get this fixed as it's very hard to work for long periods of time with the current screen settings. Please help!

---

### Post by ellgor on 2008-08-04
Hi,

Try this, System>Admin>Restricted-drivers, when the window opens check the enable box, either it will download the appropiate driver or update the existing one, if that doesnt help then try this:
check to see of you have a package called:
nvidia-settings
(synaptic) install if not, then, in a terminal type in:

gksudo nvidia-settings

I believe its the second option down (trial and error) which changes the resolution etc, hope this helps.

Regards, Ellgor.

---

### Post by theolster on 2008-08-04
Ellgor - thank you for your comments, but as stated in my original post I have attempted to install the suggested driver and have run nvidia-settings.

I also tried it using gksudo with the same effect.

Any further thoughts would be greatfully recieved.

---

### Post by tamoneya on 2008-08-04
can you post your xorg file (/etc/X11/xorg.conf)

---

### Post by theolster on 2008-08-04
I'd be happy to do so, but the problem resides on my work computer.  I haven't yet set up ssh/vpn so I can't do this until I'm back in the office on friday.

Will do so then.

---

