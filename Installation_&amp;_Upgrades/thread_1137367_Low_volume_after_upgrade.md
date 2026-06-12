---
title: "Low volume after upgrade"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by dckrooney on 2009-04-25
So I upgraded my Vista/Ubuntu laptop to Jaunty last night, and for some reason the volume of all audio playback is very faint.

I've adjusted the master volume to full as well as the in app volume controls, but it's still too quiet.

Any hints as to what's gone wrong (and how to fix it)?

Thanks in advance!

---

### Post by Dillio187 on 2009-04-25
I'm having a similar issue after upgrading to 9.04, audio was quite loud in 8.10, but now I have the PCM, Front, Headphone, and Master sliders all the way up and it's still quite a bit quieter than it used to be.

---

### Post by dckrooney on 2009-04-25
I've gone through the System->Preferences->Sounds menu and played around with various settings, and the "Test" tones are always VERY loud.
So I know the damn thing is CAPABLE of producing the desired volume...

---

### Post by Dillio187 on 2009-04-25
> **dckrooney said:**
> I've gone through the System->Preferences->Sounds menu and played around with various settings, and the "Test" tones are always VERY loud.
So I know the damn thing is CAPABLE of producing the desired volume...


I can verify that too.

---

### Post by ozPATT on 2009-04-28
for me, in 8.10, the main speakers of my dell inspiron 1525 were very quiet, but the headphones worked fine, so I didn't bother trying to fix it. Having upgraded to 9.04, both the speakers and headphones are quiet as above, so I'm in the same boat too, any fix would be great! :D

---

### Post by unempirical on 2009-04-28
Interesting.  I just upgraded from Hardy LTS to Jaunty, and the sound got much louder.

---

### Post by bond1973 on 2009-04-29
Add another to the list of no volume.  Just upgraded from 8.04 to 8.10 then immediately to 9.04 and very VERY faint volume on my Dell Latitude D830.

---

### Post by juicymixx on 2009-04-29
I'm having the 'very faint volume after upgrade' problem also.   I just upgraded from 8.10 to Jaunty, fixed all the normal upgrade issues, but this 'faint volume' problem has me stumped.

> **dckrooney said:**
> I've gone through the System->Preferences->Sounds menu and played around with various settings, and the "Test" tones are always VERY loud.
So I know the damn thing is CAPABLE of producing the desired volume...
Ditto me on that as well.   All sound seems muted or very faint EXCEPT for the "Test" tones.

Right now I'm streaming radio (thru Songbird) with all software sliders maxed out and my speaker volume knob cranked all the way, and the volume is still very faint.   Login/logout sounds, error sounds, etc. everything is very faint (even when played through the 'Sound Preferences' panel).

Anyone have any ideas?

---

### Post by juicymixx on 2009-04-30
Okay, I submitted the 'faint volume after upgrade to Jaunty' bug.   Just after submitting it I decided to check the PCM setting, and I may have come across a workaround/solution:

0) play something (streaming music, a CD, something) so you can notice the difference.
1) from the command line run: alsamixer
2) I noticed that both 'PCM' and 'Front' sliders were set low-ish.   For me, adjusting 'Front' up to 100 and 'PCM' up just a bit fixed my problem.   
Also, these sliders are 'live' so making adjustments should change the volume you are currently listening to.

Hope this helps others.  :KS

---

### Post by ozPATT on 2009-05-10
haha wow, after all this time, that actually worked for me too!! thanks heaps!

---

### Post by Das Goat on 2009-06-24
That worked for me too! Yeah!:popcorn:

---

