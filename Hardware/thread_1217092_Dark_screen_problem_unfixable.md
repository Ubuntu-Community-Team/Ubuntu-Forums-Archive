---
title: "Dark screen problem unfixable ?"
date: 2009-07-19
forum: Hardware
---

### Post by duddy67 on 2009-07-19
Hi,

I posted a month ago about a dark screen problem at the starting of my laptop 
(Emachines E520 with an Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller) : 

[http://ubuntuforums.org/showthread.php?t=1177124](http://ubuntuforums.org/showthread.php?t=1177124) 

Unfortunately the brought solutions didn't work.

add
> 
Option "FramebufferCompression" "off"
or 
> 
Option "NoDRI"
in the Section "Device" of the xorg.conf file.

The problem keeps occurring. :(

So is there an other solution for that pb or should I patiently wait 
for the next xserver-xorg-video-intel driver release ?

Thanks

---

