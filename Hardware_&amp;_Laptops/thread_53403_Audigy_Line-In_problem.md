---
title: "Audigy Line-In problem"
date: 2005-07-31
forum: Hardware &amp; Laptops
---

### Post by Dragoon_42 on 2005-07-31
I have a Hauppage PCI TV tuner that is displaying the picture wonderfully.  The TV card pipes the sound data to my Audigy's Line-In plug but I get no sound.  I know the TV card is outputting sound because I hooked it up directly to speakers and it worked fine.  I've tried hooking other sound outputs to my Audigy's Line-In and nothing worked.  

My Mixer has 4 devices Listed:
TriTech OSS
bt878 OSS
Audigy Alsa
Brooktree bt878 Alsa

I tried unmuting the line-in on my Audigy but that did not work.  Can anyone help me?
I've tried searching around the forums, but I could not find a similar problem/thread.

---

### Post by nemnivus on 2005-07-31
There are actually a few things you need to enable.  Look through the list and search for Analog Mix and put both sliders to maximum. As far as the other settings, you just need to fool around in the mixer settings to get it to work (try unmuting all the inputs, etct).  The Audigy drivers have so many settings that they're very hard to understand.  Just make sure there's something going through the input so you can tell when you hit the right switch/slider.

---

### Post by Dragoon_42 on 2005-08-01
I've tried chaning ALL of teh slider controls on the Audigy mixer, as well as the other 3 ALSA/OSS mixers to no avail.  Can anyone help me?

---

### Post by csahin on 2007-05-02
I had the same problem. I wouldn't hear anything going into my line-in. You have to turn up Line-in and Analog-Mix all the way up. Also in the Recording tab make sure the Analog-Mix-Capture is not muted (the little speaker icon at the bottom should *not* be crossed over)

---

### Post by erdizz on 2007-07-17
Turning "Analog mix" all the way up worked for me. "The problem" appeared about two years ago after a kernel upgrade. I solved it by using OSS, but now it's evident that ALSA is fine too.

---

