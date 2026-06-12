---
title: "Sound problems on r61e"
date: 2011-10-23
forum: Hardware
---

### Post by short4lif2 on 2011-10-23
I've just installed 11.10 on my Thinkpad r61e.  Everything works wonderfully except for the sound.  I followed everything in the ubuntu help files, and searched the forums for similar problems and nothing worked.  My sound device is being correctly detected and identified but still - no sound.

At one point yesterday, my sound worked only through the main lapatop speakers, but when I plugged in headphones; no sound.

Finally, I am sure that it's not a problem with the hardware itself because when I boot into Windows, the sound works.  Any help would be greatly appreciated.

Edit: The sound now works on my main speakers, but no sounnd works when i plug in headphones

---

### Post by kalliba on 2011-10-23
Did you try right clicking on the sound icon, sound settings, hardware output, select sound card?

---

### Post by short4lif2 on 2011-10-23
yeah, i only have one sound card in the list.

---

### Post by kalliba on 2011-10-23
just a thought, if you type

alsamixer

in a terminal window, next to Master, should be S/PDIF, that should be MM, if its 00, type M to change it back; see if any other settings are muted also

---

### Post by short4lif2 on 2011-10-23
I managed to get into alsamixer, and everything is turned up, but there is no S/PDIF.

---

### Post by kalliba on 2011-10-23
there's a setting for Headphones in Alsamixer also, just make sure that's not muted;

---

### Post by short4lif2 on 2011-10-23
Not to be frustrating, but there's no headphone bar either, unless there's some way to show more items that I'm not aware of.   The only items listed are Master, Speaker, PCM, Beep and Auto-Mute, which I've tried toggling without noticing a difference.

---

### Post by short4lif2 on 2011-10-24
Bump!  I have had the sound card working without having to fiddle with it in previous versions (I am returning to Ubuntu after having last used 8.04 - it's refreshing, but this problem is killing me.)

---

### Post by short4lif2 on 2011-10-25
Alrighty, I fixed it, finally, by editing /etc/modprobe.d/alsa-base.conf and adding a line at the end which reads

> options snd-hda-intel model=generic

---

