---
title: "Compaq Presario CQ61 - Strange Sound Behavior"
date: 2010-03-01
forum: Hardware
---

### Post by ZioPatcho on 2010-03-01
Hi guys, I hope you can solve my problem because it's getting me really mad! xD
I've installed Karmic and I know that the sound can't work without adding some lines to my alsa-base.conf. Opening the Sound Panel, I've noticed that the internal microphone IS WORKING! (Microphone 2 slot)(Fresh install, PULSE installed).
The internal speakers are KO.
Now I add these lines to the alsa-base.conf...

options snd slots=snd-hda-intel
options snd-hda-intel model=hp-hdx
alias snd-card-0 snd-hda-intel
options snd-hda-intel enable_msi=1

The internal speakers are now working, but the microphone IS DEAD!

What can I do to get the speakers and the internal microphone to work together?
Thanks, sorry 4 my english.

---

### Post by ozanamn on 2010-03-18
I am having the same problem..

---

### Post by khalaa01 on 2010-03-29
I'm having the same problem. I've been trying to work out a solution for a fair few hours now.

I've installed padevchooser as well, and managed to make 1 skype call before the mic stopped working again. I've even tried disabling pulseaudio with no luck - but I'm assuming this isn't the desired way to go as the volume icon then disappears?

:(

---

