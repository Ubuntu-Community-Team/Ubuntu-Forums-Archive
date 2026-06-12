---
title: "[SOLVED] Sound Jack Does not work on my Sony Laptop"
date: 2008-09-03
forum: Hardware
---

### Post by sasanpad on 2008-09-03
Hi All,

I've got a Sony Vaio VGN-FZ190 laptop and i have installed ubuntu on it. The sound only comes out my laptop speaker and when i plug in my external speakers or headphones the sound keeps coming out of the laptop speaker. I've tried so many things to fix this but still not working.
I appreciate if you could spread some light on this..
Thanks a lot

Sass

---

### Post by sasanpad on 2008-09-08
Nobody helped me on this so I have fixed it myself.
What you need to do is type cat /proc/asound/card0/codec\#*|grep Codec in the console. 
You will get something like:

Codec: SigmaTel STAC9872AK
Codec: Conexant ID 2c06

Then you check for this Conexant ID 2c06 in 
[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller) 
Find the codec that applies to your card.
Add it to the end of this file.

/etc/modprobe.d/alsa-base

Sasan

---

