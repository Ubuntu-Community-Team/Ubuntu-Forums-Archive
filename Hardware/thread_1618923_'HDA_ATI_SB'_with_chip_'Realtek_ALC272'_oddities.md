---
title: "'HDA ATI SB' with chip 'Realtek ALC272' oddities"
date: 2010-11-11
forum: Hardware
---

### Post by el_heffe on 2010-11-11
My friend has made the switch to Kubuntu x64 10.10 on his Toshiba Satellite A355D.  It has an AMD chipset and everything is working like a charm- except the microphone.  He has installed all sorts of ALSA patches, driver modules, apps to check it and more.  He is up to date on everything, but it just will not play right with the microphone.  The internal audio hardware is selected in the sound mixer, but it will not recognize any of the happiness that it should be.  Is there something we are missing?  Any advice on getting his microphone, which works under Windows, to work?  Either his internal, or preferably his external.

---

### Post by d3ngar on 2010-12-26
Yes, the same here with the Toshiba L450D.
It seems sort of random at the start: sometimes all works fine sometimes absolutely nothing works.

Sometimes some thing work and other don't.

---

### Post by ian.xerl on 2011-01-04
I have a similar problem:

After a fresh Kubuntu 10.10 (32-bit) the microphone doesn't work anymore. In KMix I see only one channel for input and output, which are at maximum volume. The mic didn't work, though.

Then, after I opened alsamixer and I turned up the volumes of the mic and micboost in alsamixer, I can hear that the mic captures sound, and plays it through the boxes. But not one application recognises the sound from the mic (I tried in skype and googleTalk plugin): they don't get the signal from the mic, while to the contrary I can hear the sound through the boxes!

Sound card: HDA ATI SB
chip: Realtek ALC883

What to do?

---

