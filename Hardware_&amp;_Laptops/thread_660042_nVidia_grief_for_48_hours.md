---
title: "nVidia grief for 48 hours"
date: 2008-01-06
forum: Hardware &amp; Laptops
---

### Post by Peter09 on 2008-01-06
Can anyone help with a new GeForce 8600 on my new PC. 
I bought a new PC to replace my old Ubuntu machine, and was able to transfer the disk straight from the old machine to the new one with very few issues except one.:confused: I have been struggling to get my Nvidia card to work.

Basically, as soon as I start the Xserver with the nVidia driver enabled I get a black screen with no recovery. I hear a fan slow down, (most probably the graphics card fan) and thats it.

I have tried Envy and also downloaded the latest driver from the nVidia site and run the executable - same symptoms both times.

Where to go from here?

---

### Post by overdrank on 2008-01-06
> **Peter09 said:**
> Can anyone help with a new GeForce 8600 on my new PC. 
I bought a new PC to replace my old Ubuntu machine, and was able to transfer the disk straight from the old machine to the new one with very few issues except one.:confused: I have been struggling to get my Nvidia card to work.

Basically, as soon as I start the Xserver with the nVidia driver enabled I get a black screen with no recovery. I hear a fan slow down, (most probably the graphics card fan) and thats it.

I have tried Envy and also downloaded the latest driver from the nVidia site and run the executable - same symptoms both times.

Where to go from here?

HI and did you uninstall the previous drivers before installing with Envy? Also are you able to boot into recovery mode and use startx command?

---

### Post by Peter09 on 2008-01-06
All drivers have been uninstalled / installed many times :mad: but no difference. I normally boot straight to the command line so I usually login and type startx any way. The boot is normal with no problems and the system behaves ok until I type startx. Then .... gone.

---

### Post by Yellow Pasque on 2008-01-06
Please post the following (remember to use [ code ] blocks)

/etc/X11/xorg.conf and /var/log/Xorg.0.log

---

### Post by Peter09 on 2008-01-07
Update on this:

My son has the same card in his machine, which runs Vista. So I decided to swap them to see what happened and to exclude a H/W problem .... by now you will have guessed, his card works in my machine, my card does not work in his machine, same symptoms. So its a trip back to the store today to get a replacement.

Turns out to have been 48 hours concentrating on the wrong problem :confused:

---

