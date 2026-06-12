---
title: "Problems configuring OSMesa-7.2"
date: 2009-05-28
forum: Installation &amp; Upgrades
---

### Post by wavepeak on 2009-05-28
New to the board:

I am trying to install and run Gerris a CFD package using Ububtu 8.10 on a Velocity VSC-135
(and) I am having trouble installing OSMesa-7.2 or more exactly reinstalling the DRIGL

Upon  running  ./configure  in the Mesa folder  I get the following issue 
__________________________________________________________________________________
checking for LIBDRM... yes
checking for DRIGL... configure: error: Package requirements (x11 xext xxf86vm xdamage xfixes) were not met:

No package 'xxf86vm' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables DRIGL_CFLAGS
and DRIGL_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
____________________________________________________________________________________

I have tied to reinstall DRIGL but? I am stumped.   

One note: I am using NVIDIA 9800 GT  and using there cuda drivers for multi processer operations +/-   

Foot note: I am new to linux / and I need to still learn C++  so I apploigize if this is a dumb question.
Thanks to anyone who could lead me in the right direction.

---

### Post by Partyboi2 on 2009-05-30
Hi, looks like you can install it from the ubuntu repos instead of having to compile it. You can either search synaptic for libosmesa6 and install it or open a terminal and install with
```
sudo apt-get install libosmesa6
```


When compiling if you see something like

> checking for DRIGL... configure: error: Package requirements (x11 xext xxf86vm xdamage xfixes) were not met:

No package 'xxf86vm' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.
it means you need to install the missing packages and normally the dev versions of that package so for xxf86vm you would need to install libxxf86vm-dev.

****

---

### Post by wavepeak on 2009-06-01
Thanks:

Yes manually install sometimes is not the way to go! ( I chased the software errors) but did not stop to read the error itself (A missing package)  Thanks for your time. I feel kind of dumb.

 I letting Ubuntu reinstall the PKG + version 6X of Mesa via the apt-get and it was just the ticket I ca now compile gfsview and it seams to be running.

Thanks again!

Some times it is hard to see the forest for the trees+/-

---

