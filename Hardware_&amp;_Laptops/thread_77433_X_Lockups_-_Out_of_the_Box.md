---
title: "X Lockups - Out of the Box"
date: 2005-10-16
forum: Hardware &amp; Laptops
---

### Post by jrnewquist on 2005-10-16
3 lockups in my first 5 hours running Breezy Badger.

I have a default 5.10 install on a Dell Inspiron with an nvidia 6800 graphics card.  I have NOT installed any special drivers.  I do not have "RenderAccel" statements, or anything like that in my /etc/X11/xorg.conf, as is mentioned in a long thread about lockups in the 5.04 forum.

Here's the pertinent section of /etc/X11/xorg.conf...


```
Section "Device"
        Identifier      "NVIDIA Corporation NV40 [GeForce 6800 
                        Ultra/GeForce 6800 GT]"
        Driver          "nv"
        BusID           "PCI:1:0:0"
EndSection


```
Are there some more stable, even bare bones, graphics drivers I can use?  Is there some other possible solution to the problem?

Thanks,
-Jason

---

