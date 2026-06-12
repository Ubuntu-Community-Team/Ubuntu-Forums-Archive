---
title: "No sound out of speakers/ wifi drop outs after ubuntu update HP dv5-1235 dx"
date: 2009-07-22
forum: Hardware
---

### Post by maz91379 on 2009-07-22
So after a routine update my sound stopped working. I thought a reinstall would fix the problem so i took the opportunity to install ubuntu studio. 
The problem wasn't solved and now my wireless drops in and out.  

I get sound out of  my headphone jack from a software synth but not from streaming videos or basically anything else. Also i can only hear sound from one program at a time. For example if i start Hydrogen(a drum machine) i can hear it through the headphone jack. But if i start the synth after, i don't and the other way around.Even if i close one of the programs i can only hear the first program i started until i restart. 

Any help would be appreciated.

---

### Post by maz91379 on 2009-07-22
Alrighty so after doing 
"sudo gedit /etc/modprobe.d/alsa-base.conf"
and adding" options snd_hda_intel model=hp-dv5 "
 sound seems to work however i can still only get sound from one music production program at a time.

---

