---
title: "No sound in HP G60-120US"
date: 2008-12-06
forum: Hardware
---

### Post by Epilonsama on 2008-12-06
My new notebook is making static everytime there suppose to be sound, I think the audio chipset is an nvidia one, any hel will be appreciated.

I think the problem is related to my ALSA module.

---

### Post by mschap on 2008-12-19
I am having the same problem with this machine.  Any help would be appreciated.

---

### Post by hardtke on 2009-06-05
If you get sound from the headphone jack but not the built in speakers, try edit the this file:

sudo gedit /etc/modprobe.d/alsa-base.conf

Add the following line:

options snd-hda-intel model=laptop enable=1 index=0

Restart the computer and it should work.

---

