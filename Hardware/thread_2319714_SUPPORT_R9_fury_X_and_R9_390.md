---
title: "SUPPORT: R9 fury X and R9 390"
date: 2016-04-06
forum: Hardware
---

### Post by nigro.orlando on 2016-04-06
Hi!
Right now I'm using a Radeon r9 390 and I'm running Debian with kernel 4.3. I had Ubuntu before but I ended up with Debian while trying different Ubuntu versions because I had, and I still have a problem with my Granada GPU. Is the DPM, that is bugged. Desktop freezes if I leave the DPM in auto, but It doesn't if I change to low or high. (I have experienced the problem a couple of times even after I used the command, but much later).
I tried a lot of solutions (new firmware, newest mesa etc.) and it's ok right now but not optimal at all. Now I'm trying to disable the DPM changing the /etc/default/grub to see what happens. 

I don't use Linux for gaming, I have a Windows partition for it but I'd like to use the Linux partition smoothly, since is the one I use the most. My goal is not to have outstanding performances but just not to have the desktop freezing, and be able use DE like Kde or Gnome.

My question is, If I upgrade my GPU to the R9 Fury/R9 fury X (which I intended to to sooner or later), will they be better supported then the actual one I have now? How is the GPU working right now on Ubuntu? Problems?
I have been reading a lot about the AMDGPU drivers to be very good but I also read that is a driver optimized for card like the Fury rather then the r9 390? Is it so? 
Will Ubuntu 16.04, thanks to new driver and kernel, handle the r9 390, or the r9 fury X better?

---

### Post by QIII on 2016-04-06
The R9 390 does not have a Volcanic Islands chip to take full advantage of AMDGPU.  There is a whole lot of messing around to be done to get the experimental support working.

The R9 Fury has a Fiji chip that works OOTB with AMDGPU.  I the R9 380 comes with the Tonga chip, which also works with AMDGPU.

So be careful:

390 - no workie
380 - works

It's not the higher number, it's the chipset.

---

### Post by nigro.orlando on 2016-04-10
I see, thank you for your answer.

Yes, I read about this important differences among the chips. I'm indeed using the radeon driver on debian right now and as I understood from your answer if I don't do the hardware upgrade I will still have to keep using it.

Does the r9 fury x work good as you described allready now with Ubuntu 15.10 or should I wait the release of the 16.04?

---

### Post by nigro.orlando on 2016-04-22
I did the upgrade and I'm running now Ubuntu Gnome 16.04 with the fiji card fury X. As you said is working very well, no problem with the desktop at all!

---

