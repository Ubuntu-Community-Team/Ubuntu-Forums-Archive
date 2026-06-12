---
title: "(GL) direct rendering, is that 3d acceleration??"
date: 2007-05-16
forum: Hardware &amp; Laptops
---

### Post by porphiron on 2007-05-16
lo folks,

I can see this whole accelerated driver thing with my laptop 9100 IGP is going to be a thorn in my side but, feh.....so far i have managed to get it to use direct rendering (GL)

i could have gone on to install and setup beryl, which uses 3d acceleration, so I would have thought the setup i've used (take any setting up an old ati card w/ beryl howto), would have setup the whole nine yards but this doesnt seem to be the case.

Trying to run cedega, so i can play a few of the games i had originally installed, i get a green light against the direct render test, but a red against 3d acceleration, now obviously open gl is a seperate entity, but surely this means that 3d acceleration is not available, even when i'm using the "radeon" driver in the xorg.conf.


am truly going to rip a limb off an beat myself sensless soon :mad:

---

### Post by encompass on 2007-05-17
It may have changed... but I have the 9100 IGP and they say there is no support in linux for the rendering.  FRom the ATI site that is.  As for radeo driver... try running something like glxgears... and report your frame rate.

---

### Post by porphiron on 2007-05-17
thanks for the reply!

this is interesting.....

before enabling direct render glxgears was hitting the 640fps, now its saying 1425fps

tried armagetron and that work fine with a fps of around 60

chromium around 50

some sort of acceleration must be at work, so why cedega is saying that 3d acceleration isnt working but yet gl rendering is, is a mystery :confused:

(i just thought they were one and the same?)

go figure......

---

