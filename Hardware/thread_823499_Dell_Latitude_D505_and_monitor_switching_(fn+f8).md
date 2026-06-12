---
title: "Dell Latitude D505 and monitor switching (fn+f8)"
date: 2008-06-09
forum: Hardware
---

### Post by larseko on 2008-06-09
Hi,

There are numerous topics regarding this issue, but I haven't been able to solve my problem yet. 

I have several Dell Latitude D505 laptops with intel 82852/855GM graphics controllers. In both ubuntu 6.06, 7.04 and 7.10 I had toggling of external display with  fn+f8 working, but after upgrading to Hardy this is no longer possible. Now it will only work to use an external display if it's connected before startup, and even then I'm not able to switch between the two, instead they are both active. 

The experimental intel driver is installed. In the Xorg.0.log file it says the /usr/lib/xorg/modules/drivers/intel_drv.so is used. I'm not sure if this is the correct one, but I think so? 

I have looked into i810switch, but would prefer a solution with the fn+f8 keys. This is a neccessary fix before we can upgrade to Hardy on several schools here, so I'm grateful for any help.

Just say the word and I'll post more info.

---

### Post by larseko on 2008-12-17
So, am I the only one experiencing this problem with the latitude series/this graphics controller?

---

### Post by larseko on 2008-12-18
Ok, I fixed this partially, by letting X generate a new xorg.conf by running /etc/X11/X -configure as root. Now it works the same way as before, which is more convenient, but still with something to be desired. Hen I only have the external monitor (projektor) active, the mouse pointer will look strange, as if it was only 16 or 256 colors, and when both LCD and projector are active, there will be some... jitter, or disturbances across the monitor (a moving jigsaw pattern, like sharp waves).

Has anyone else experienced this?

---

