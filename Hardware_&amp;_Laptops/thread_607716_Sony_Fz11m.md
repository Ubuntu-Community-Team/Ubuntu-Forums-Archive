---
title: "Sony Fz11m"
date: 2007-11-09
forum: Hardware &amp; Laptops
---

### Post by hzsolti on 2007-11-09
Somebody please help me!

A cant start my motion eye camera... and my microphone (build-in, and line-in too) :(
An other problem is that I cant set my brightness...
:cry::confused:

THX 4 ALL

---

### Post by hzsolti on 2007-11-14
Ok I have solved my problem... motion eye camera is working (better quality than in Windows :) )
and the microphones are working :)

So only the brightness, what I cant set with the fn keys....
But Im on it...

---

### Post by Znort_Ubern00b on 2007-11-14
can you post how you sorted your microphone...i'm having probs sorting mine out.

Cheers

---

### Post by hzsolti on 2007-11-15
So,
I have compliled the newest alsa...
then open the terminal and type there:

sudo gedit /etc/modprobe.d/alsa-base

To that file add to the end this line:
options snd-hda-intel model=vaio

If you are ready, istall the GNOME ALSA MIXER....
Lauch it!

You will see 2 checkboxes on the bottom:
- Mic Jack
- Internal Mic

Select wich you want to use....
:)

---

