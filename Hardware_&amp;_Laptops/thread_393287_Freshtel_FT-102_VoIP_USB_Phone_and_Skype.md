---
title: "Freshtel FT-102 VoIP USB Phone and Skype"
date: 2007-03-25
forum: Hardware &amp; Laptops
---

### Post by jfdarv on 2007-03-25
Hi, I have in my possession a USB Phone and I experience problems with the sound quality in Skype. I do hear the sound test and I'm able to record my voice as well but the sound is too choppy. The sound in Skype works ok with my on-board sound car so I think the problem is just a matter of misconfiguration.

Does anyone know either I have to create a .asoundrc file and how do I configure it ?

The phone is a ```
Freshtel FT-102 VoIP USB Phone
```

I can't play a file with aplay neither.

```
$ aplay -D hw:1,0 file1.wav
Playing WAVE 'file1.wav' : Signed 16 bit Little Endian, Rate 44100 Hz, Stereo
aplay: set_params:906: Channels count not available

$ aplay -D hw:1,0 file2.wav
Playing WAVE 'file2.wav' : Unsigned 8 bit, Rate 7418 Hz, Mono
aplay: set_params:901: Sample format not available
```

Thanks to whoever might have a clue about my problem.

---

### Post by super.rad on 2007-11-05
I have the same usb phone and the sound is terrible aswell, anyone know a fix?

---

### Post by dundel on 2008-04-09
I have this USB Phone to. But I can't get it to be recognized by Gutsy.
When i run *lsusb*, I can see it. But when I run *cat /proc/asound/cards* it's not showing up.
Does anybody know how to fix this. Because it did work on Feisty Fawn.

---

