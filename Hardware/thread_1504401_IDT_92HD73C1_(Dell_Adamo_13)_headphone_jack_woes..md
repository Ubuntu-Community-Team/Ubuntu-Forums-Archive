---
title: "IDT 92HD73C1 (Dell Adamo 13) headphone jack woes."
date: 2010-06-07
forum: Hardware
---

### Post by hxcobd on 2010-06-07
Simple problem: the headphone jack just doesn't seem to work at all on my Dell Adamo 13.

Yes, I've switched it to the headphone jack in both the ALSA panel as well as the PulseAudio volume control.

Any suggestions? I'm hoping to not have to recompile a patched ALSA, that seems rather overkill for such a simple problem.

*edit- The sound card shows up as HDA-Intel in ALSA, if that helps.

---

### Post by woodpush on 2010-09-30
hey did you end up finding a solution to this? just got my adamo today and have the same problem. headphone jack not working

---

### Post by woodpush on 2010-09-30
Found the solution: just follow the first part of [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) and add options snd-hda-intel model=dell-m6 to the /etc/modprobe.d/alsa-base.conf file.

This should enable the microphone and the headphone jack for the Dell Adamo 13.

---

### Post by sagara on 2011-01-20
Thanks for the tip! this worked like a charm ^_^

Both the microphone and headset are working now.

---

