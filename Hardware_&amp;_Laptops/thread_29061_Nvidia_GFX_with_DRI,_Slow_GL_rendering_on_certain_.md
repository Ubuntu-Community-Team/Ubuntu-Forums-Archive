---
title: "Nvidia GFX with DRI, Slow GL rendering on certain resolutions"
date: 2005-04-22
forum: Hardware &amp; Laptops
---

### Post by zafar on 2005-04-22
Hello,
I'm running a fresh Hoary install and i have a Geforce 2 MX working using the Nvidia drivers in the ubuntu repo. It is configured and DRI is enabled. The desktop resoultion is set to 1280x1024@85hz.
When using any OpenGL app or screensaver, they run fast when it is windowed, but when screensavers came on they would run at around 1 fps. After expirementing with an OpenGL Music Visualization in amarok, i found out it works fast until the window is resized to any window greater than a 1008x738 window. When it is that size it works fast and is smooth, but if you resize it to even one pixel greater than that, the frame rate drops to around 1fps. The same thing happens with glxgears after it is resized to greater than 1014x909.
I have no idea why this happening.. and from searching the forums i've seen some other people have the same problem but there hasn't been a resolution yet. Any help is appreciated.

---

### Post by PaRRoT.it on 2005-04-22
[QUOTE=zafar]Hello,
I'm running a fresh Hoary install and i have a Geforce 2 MX working using the Nvidia drivers in the ubuntu repo. It is configured and DRI is enabled. The desktop resoultion is set to 1280x1024@85hz.
When using any OpenGL app or screensaver, they run fast when it is windowed, but when screensavers came on they would run at around 1 fps. After expirementing with an OpenGL Music Visualization in amarok, i found out it works fast until the window is resized to any window greater than a 1008x738 window. When it is that size it works fast and is smooth, but if you resize it to even one pixel greater than that, the frame rate drops to around 1fps. The same thing happens with glxgears after it is resized to greater than 1014x909.
I have no idea why this happening.. and from searching the forums i've seen some other people have the same problem but there hasn't been a resolution yet. Any help is appreciated.[/QUOTE]
 Your GF2MX is the problem.
It's slow on certain res for hardware limitation.

800x600 is best res for this card.

---

### Post by zafar on 2005-04-22
No, that isn't the problem. This is the glx output running at more than half the full screensize.

186 frames in 5.0 seconds = 37.200 FPS
187 frames in 5.0 seconds = 37.400 FPS
After i make the window just 1 pixel wider, this is the fps.
68 frames in 5.0 seconds = 13.600 FPS
8 frames in 5.0 seconds =  1.600 FPS
6 frames in 5.0 seconds =  1.200 FPS

Also, i use to use Fedora Core 3 before Ubuntu with the same hardware, and the screensavers use to run fine on it with the same resolution. Now it runs at 1fps fullscreen.

---

### Post by PaRRoT.it on 2005-04-23
Uhm... search in /etc/X11/xorg.conf if you use "nv" o "nvidia" module.

---

### Post by zafar on 2005-04-23
I said in the originial post that DRI was enabled. Anyways, 'nvidia' is in my xorg conf

```

Section 
"Device"         Identifier      "NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
Driver          "nvidia"         
BusID           "PCI:1:0:0" 
EndSection

```

---

### Post by 9Panther on 2005-04-30
I also have the same problem with OpenGL on 2 different pcs, with a GeForce3 & 4.

---

### Post by zafar on 2005-04-30
phew.. so it's not only me. I'm not sure what else we can do here. So far we haven't gotten any real technical repsonses to fixing it. Should I file a bugzilla bug report?

---

### Post by zafar on 2005-05-11
*bump*

---

