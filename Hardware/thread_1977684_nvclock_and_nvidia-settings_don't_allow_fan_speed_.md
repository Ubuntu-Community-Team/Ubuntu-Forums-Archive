---
title: "nvclock and nvidia-settings don't allow fan speed change"
date: 2012-05-10
forum: Hardware
---

### Post by ammut on 2012-05-10
My graphics card fan decided to make a really annoying noise and I'm trying to slow down the fan (I do not care if it overheats a bit).  Currently it is at 30% speed as stated by nvidia-settings.  I have added an option to my xorg.conf file of CoolBits, set to a value of 5, which in theory should allow me to change the fan speed.

Now when I try to adjust the fan speed, then hit apply, it simply goes back to 30% as if I made no changes at all.  I cannot change it from the command line or the gui.

I also installed nvclock, but whenever I try to pass an option to it I get a segfault.  

I am very close to just scrapping this card and getting a passively cooled version so I don't have to deal with this noise.  Any help would be appreciated at this point, before I go out and spend another $50.

---

### Post by d4m1r on 2012-07-16
Try coolbits value of 4.

---

