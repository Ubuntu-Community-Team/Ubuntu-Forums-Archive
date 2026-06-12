---
title: "ISA/PNP azt1008 soundcard?"
date: 2005-06-23
forum: Hardware &amp; Laptops
---

### Post by ions on 2005-06-23
Has anybody succeeded in getting to work an ISA/PNP azt1008 soundcard?

I tried asking in this thread: [http://www.ubuntuforums.org/showthread.php?p=225930#post225930](http://www.ubuntuforums.org/showthread.php?p=225930#post225930) but got no answer.

---

### Post by wvslkr on 2005-06-24
I'm not sure that this will help, but lets give it a shot.  I am not sure which module this card uses. The azt2320 module is listed in the kernel modules,but a google on the card  showed the ad1848 module for it.  My suggestion try:

sudo modprobe snd-azt2320 or sudo modprobe snd-ad1848.

Try both and if one is accepted without errors then it is probably the right module.
If one works you will then have to open /etc/modules.conf in an editor and add the line snd-whicheverworks isapnp=0.  This makes it so the card is enabled at boot-up. 

Even if the card is enabled you may still need to make some adjustments to get things playing correctly.  I believe the User Guide and or How To's will cover you there.

GL.  Hope it helps. :)

---

