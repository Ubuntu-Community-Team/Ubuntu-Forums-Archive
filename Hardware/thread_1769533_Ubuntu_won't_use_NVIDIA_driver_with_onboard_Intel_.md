---
title: "Ubuntu won't use NVIDIA driver with onboard Intel graphics present"
date: 2011-05-28
forum: Hardware
---

### Post by topofmurrayhill on 2011-05-28
I installed Ubuntu on an old Dell box to use it as a development machine, plus I added a GeForce 6200 PCI video card for Unity and whatever. However, when I try to use the proprietary NVIDIA driver (the 'nvidia-current' package) the system still boots with a generic vesa driver (I ran compiz-check). In the Additional Drivers app the NVIDIA driver is lit green and says "activated but but not currently in use."

I think it's getting confused by the old Intel integrated graphics hardware in this machine. Unfortunately there doesn't appear to be a way to disable it. The only BIOS video options are "Onboard" and "Auto" and it's set to Auto. The monitor is plugged into the NVIDIA card, which is working but only with the generic video driver.

Is there any way to force Ubuntu to use the NVIDIA driver?

---

### Post by e-Gee on 2011-05-28
Typ in terminal  

sudo nvidia-xconfig

and restart computer.

---

### Post by topofmurrayhill on 2011-05-28
> **e-Gee said:**
> Typ in terminal  

sudo nvidia-xconfig

and restart computer.

Thanks, that was serious progress. Now I'm seeing the right driver but unfortunately getting a blacklisted gpu error:

Gathering information about your system...

 Distribution:          Ubuntu 11.04
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation NV44A [GeForce 6200] (rev a1)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [WARN]

Something potential problematic has been detected with your setup:
 Warning: PCI ID 8086:2562 detected.

---

### Post by topofmurrayhill on 2011-05-28
BTW I did bypass that in case it wasn't legit, but my goal is to see my session come up with Unity and so far it's still the regular Gnome desktop.

ADDED: As far as I can tell, the following output represents where I'm currently stuck (see arrow). Not sure why a GeForce 6200 card would come up with a blacklisted GPU.

$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 6200/PCI/SSE2
OpenGL version string:  2.1.2 NVIDIA 270.41.06


 Not software rendered:    yes
Not blacklisted:          no  <====
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes
 

Unity supported:          no

---

### Post by topofmurrayhill on 2011-05-29
The resolution I settled on was to add UNITY_FORCE_START=1 to /etc/environment. Since the NVIDIA driver was properly installed and the hardware was working, all I really needed was to circumvent the compatibility check and be able to try out Unity. That did the trick.

I don't know if the blacklist involved my video card or the presence of the integrated Intel graphics that I couldn't disable, but I think it was a spurious issue. Everything seems to be running just fine with the GeForce 6200 PCI card.

I'm using the nvidia-current driver package and it still says "activated but not currently in use" in the Additional Hardware app, but this is apparently a known (and misleading) bug.

---

