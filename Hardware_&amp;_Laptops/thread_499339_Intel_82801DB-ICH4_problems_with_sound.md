---
title: "Intel 82801DB-ICH4 problems with sound"
date: 2007-07-12
forum: Hardware &amp; Laptops
---

### Post by jmagick07 on 2007-07-12
I can't get any sounds out of my speakers, using the sound card Intel 82801DB-ICH4 on a Gateway laptop computer.

I tried looking in the alsamixer a bunch of times, but still can't get sound.  I've had this problem for a while now, and don't know a way to get it to work.

---

### Post by jmagick07 on 2007-07-12
Has anyone with this sound card gotten it to work?

---

### Post by fredj on 2007-07-12
Open a terminal and type
cat /proc/asound/card0/codec\#*
This will tell you the name of the soundchip that is used on your particular card and you can then search 
for possible solutions for that soundchip. With regard to alsa mixer make sure that you have added all the
volume controls and switches, both for play and record.

---

### Post by jmagick07 on 2007-07-12
Well this is the info I got from the mixer

Card: Intel 82801DB-ICH4                                                     
Chip: Conexant id 30

But I couldn't find much on that chip

---

