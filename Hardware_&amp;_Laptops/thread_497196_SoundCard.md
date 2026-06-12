---
title: "SoundCard"
date: 2007-07-10
forum: Hardware &amp; Laptops
---

### Post by Dr Zolygon on 2007-07-10
I have a creative x-fi card but i know that creative does not have any drivers yet. I would atleast like to be able to use my onboard audio which is,

Realtek ALC883.

Does anyone know how to get this working?

Any help is appreciated.

---

### Post by fredj on 2007-07-10
Make sure that it's enabled in the bios. Double click on the volume control to open the alsa mixer.
Under File ->Change Device make sure the correct device is selected. Then under edit preferences
add all the appropriate volume controls for playback and record and add all the appropriate switches
as well.
If it still doesn't work do a yahoo search for that chip and linux to see if you need to add any options lines
to the alsa-base file in /etc/modprobe.d

---

