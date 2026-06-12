---
title: "Integrated speakers don't work, headphones work fine"
date: 2006-11-25
forum: Hardware &amp; Laptops
---

### Post by Xtyn on 2006-11-25
I just installed Ubuntu 6.10 on my LG LW 60 Express laptop and I can hear sound only through the headphones or external speakers, not through the integrated ones. In windows they work, I have dual boot. I tried some stuff that I found on the forum but nothing worked. I tried reinstalling the Alsa driver, configuring it, nothing. In fact, the integrated speakers don't work on any distro I tried so this must be a difficult one. My sound card is from C-media. I believe it's C-media high definition audio 9880L. Hope you can help me guys...

---

### Post by Xtyn on 2006-12-01
Come on, can anybody help me?

---

### Post by christhemonkey on 2006-12-01
Are they enabled in the BIOS?


Hmm i guess they must be as you said they work in windows...

Have you checked awny relevant options in Volume Control?

---

### Post by Xtyn on 2006-12-02
I don't have many options in volume control, I believe it's becase my soundcard is not properly recognized. I tried lots of things in volume control, none work. Thanks for posting.

---

### Post by muximus on 2006-12-02
hey i m facing the same problem.. i hv got a hp pavilion with intel hda audio.. headphones or speakers connected to the jack work just fine.. but nothing frm the onboard speakers.. makes it a little inconvenient when travelling.

ne ideas??

---

### Post by Xtyn on 2006-12-02
Well, I believe we need the driver for our soundcard. snd-hda-intel just is not good enough to make everything work fine. I have too little options in kmix or in alsamix for that matter. Well, for my soundcard, I need the CMI9880 driver I believe. On the ALSA site I didn't find it, just some vague CMI8768 and some other stuff that I didn't really try to install. Maybe, in the end, I will try to install the CMI8768 driver, just to see if something works.

---

### Post by Xtyn on 2007-03-02
I solved my problem thanks to this thread [http://www.ubuntuforums.org/showthread.php?p=2237438#post2237438](http://www.ubuntuforums.org/showthread.php?p=2237438#post2237438)

---

