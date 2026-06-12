---
title: "Nforce2 and the sound of silence !!"
date: 2005-03-31
forum: Hardware &amp; Laptops
---

### Post by MrGrumpy on 2005-03-31
Ok not quite silence but no sound on desktop nor in games, however !!!!! I get sound in the various media players, ie amarock, VLC etc. The one I`m more interested in is the games one I get the following error :-

device /dev/dsp can't be opened (Cannot allocate memory)

Now I`m not alone with this from what I`ve searched but the answer on some posts seems to be *killall esd* this does nothing as it comes back with *esd: no process killed* ???  Is their a resolution to this as my next move is to dump this onboard sheet and stick my SB Live back in ! If I was to go down this road is it pretty straight forward, would it work right from the start ?? Now I know my onboard sound works in other linux distro`s Mepis as an example so a bit confused. I shouold add that i installed the nforce drivers from nvidia to try and resolve but still no show. Any advice from those whom have been down this long winding road.

TIA

Ali

---

### Post by bobmitch on 2005-03-31
This isn`t a problem with your hardware - so buying an sblive or whatever won`t help.  The problem is that ubuntu are having issues with their choices of sound services.

We have gone from esd -> gstreamer and back to esd again.  It sounds to me like you are still using gstreamer somehow, but the system sounds are attempting to use esd.

I regularly have to kill esd to get sounds in multimedia application - it looks like you have the same problem - in reverse. :)

Canonical devs are in a much better position to give accurate and non-misleading information than I am, so hopefully one of those kind souls will reply.

---

### Post by MrGrumpy on 2005-03-31
Fair enough I await with bated breath  [-o<  Might try the SBLive anyway, its been sitting in the parts box for long enough now.

Ali

---

### Post by bobmitch on 2005-03-31
[QUOTE=MrGrumpy]Fair enough I await with bated breath  [-o<  Might try the SBLive anyway, its been sitting in the parts box for long enough now.

Ali[/QUOTE]

Just noticed you are from Fife - hello neighbour. :D

---

### Post by MrGrumpy on 2005-03-31
Not a born and bred fifer :) but my family is all from Buckhaven,Methil  :razz: 

Ali

---

