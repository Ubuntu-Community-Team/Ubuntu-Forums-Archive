---
title: "Only one speaker playing"
date: 2006-10-06
forum: Hardware &amp; Laptops
---

### Post by Jebenko on 2006-10-06
Hello,
   after a apt-get update and apt-get upgrade I had many problems...
 (no kde, no sound, ati driver gone...)
  I restored my system from backup and the sound was not working.
 
 I compiled and installed the alsa driver. All is working fine but only one speaker is playing. The cables are ok. If i connect headphones there is also only one playing. But if i disconnect the audio cable from the notebook both internal speakers are playing.   I have Dell D610
 
 aplay -l
 **** List of PLAYBACK Hardware Devices ****
 card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
   Subdevices: 0/1
   Subdevice #0: subdevice #0
 card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
   Subdevices: 1/1
   Subdevice #0: subdevice #0
 
 
  It was all working fine a few hours ago. 
 
 Any ideas?

---

### Post by Jebenko on 2006-10-07
Hello,
  working now.  Alsamixer does something like this:

alsamixer: relocation error: alsamixer: symbol snd_mixer_selem_get_playback_dB, version ALSA_0.9 not defined in file libasound.so.2 with link time reference

But alsamixergui is working and the sound level can be adjusted.

---

