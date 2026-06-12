---
title: "Sound issues on dell XPS M1710"
date: 2009-11-16
forum: Hardware
---

### Post by Madals on 2009-11-16
This is a fresh install of ubuntu 9.10 on a duel boot with vista. 
Ever since the install, there has been an issue with the sound balance when trying to change the volume. 
Using the main volume slider, until 3rd step off mute there is no sound. At the 3rd step, volume is full in the left speaker, and there is no sound in the right speaker. Increasing the volume further normally increases volume in the right speaker, but it stays maxed in the left (although at max volume, the right speaker is slightly louder). 
Using the volume slider in applications adjusts the volume equally as would be expected. 

Changing the balance is system -> preferences -> sounds has no effect until full volume, at which point it needs to be set slight to the left to balance it correctly

It is an integrated sound card. 
Any idea's?
Madals

---

### Post by jleedixon on 2009-11-16
I also have an XPS M1710.  For me, sound only comes through the internal (bottom) speaker, not through the front speakers.  I found that if I play with the command-line tool "alsamixer", I can adjust things to where I can hear the front speakers.  When using the gnome sound controls, the volume levels in alsamixer change but in strange jumps.

Something is not configured right for this sound card.  It worked great under ubuntu 8.10.

---

### Post by jleedixon on 2009-11-17
Finally got it working based on something I found here:

[http://ohioloco.ubuntuforums.org/showthread.php?t=1284627]("http://ohioloco.ubuntuforums.org/showthread.php?t=1284627")

Specifically, I added this to the end of /etc/modprobe.d/alsa-base.conf
options snd-hda-intel model=ref

And then rebooted.  Walla.

---

### Post by Madals on 2009-11-18
Thank you jleedixon! Will give this a go and hopefully it will work :D

---

### Post by Danish989 on 2011-02-11
Well, did it? I have the same problem - sound only out of right speaker, and I too own a Dell XPS.

---

