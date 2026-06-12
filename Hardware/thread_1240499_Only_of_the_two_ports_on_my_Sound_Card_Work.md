---
title: "Only of the two ports on my Sound Card Work"
date: 2009-08-14
forum: Hardware
---

### Post by abi0909 on 2009-08-14
I have a Dell XPS M1330. The sound card in my laptop has 3 ports : 2 ports for headphones and 1 port for MIC. But out of the 2 ports for headphones, only one works. If I plug in my headphones on the other port, there is no sound from my headphones. But still the speakers get muted once I plug in my headphones on the second port. 

Any help on this is appreciated. 

Thanks,
Abi

---

### Post by nixscripter on 2009-08-15
You might want to check your mixer levels. The second port might be muted.

Use the **alsamixer** command line utility is my suggestion. Use up and down arrows to adjust volume, M to toggle mute.

---

### Post by tarunmittal_86 on 2009-09-05
heyy.. i had similar problems few days back.. I have got a dell xps M1530,  i resolved the issue u have: 
go to volume control by right clicking the volume button (usually top right), click on preferences, use HDA Intel (Alsa Mixer) from combo box, click on prefernces, select following checkboxes: 
Master, PCM, Front, Surround, Center, IEC958 Digital Playback Source, digital input source
you'll get volume controls for these, increase volumes to MAX for all..

It worked for me, hope it works for you too, now i have another problem, only one headphone jack works at a time, and both won't work simultaneously. if u get any help with this issue to kindly update.

---

