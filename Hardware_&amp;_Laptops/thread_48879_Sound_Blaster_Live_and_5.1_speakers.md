---
title: "Sound Blaster Live and 5.1 speakers"
date: 2005-07-14
forum: Hardware &amp; Laptops
---

### Post by ra1n on 2005-07-14
Hi
Someone has been able to use 5.1 speakers with a sound blaster live in hoary?
The speakers works, but only in 4.0, I cannot hear anything from the center channel, and I cannot find a way to enable it.
I'm using the latest packaged kernel with alsa (the default configuration of hoary)
thank you

---

### Post by l.tambiah on 2005-07-15
I use soundblaster audigy 7.1 and can hear every little sound out of the speakers. You need to open a terminal and type : alsamixer.

Ensure all channels are turned up and unmuted in the alsamixer application. Then test your sound.

---

### Post by Deathpickle on 2005-07-15
Yes I think by default the center channel is dsiabled.

What you need to do is run alsamixer from a terminal (as sudo) then unmute your center channel and turn it up. Once you do that BE SURE to exit out and type (also as sudo) alsactl store otherwise when you reboot your settings will go back to defaults.

---

### Post by endy on 2005-07-15
A quick test I used for my 5.1 speakers was as follows:

```
speaker-test -c6 -D surround51
```

man speaker-test for more info :)

---

### Post by TristanMike on 2005-08-17
Hi, "endy" thanx for the sound test command, I haven't seen that command. I used it and tested my speakers and I have a couple of quick questions if I may to anyone that can help. I'm still very new to this whole Linux thing.

I ran the test and found that sound is, in fact, getting to my rear speakers (something I didn't think was happening. But when it tested the center speaker, the sound came from my Front Left speaker, very loud, and the LFE (what is that?) came from the front right, low. could someone please explain why this is. The settings for the speakers in alsamixer are all set to 100%

Also, I use the default music player with Ubuntu, Rhythmbox 0.8.8 and I can't get the sound out of the rear speakers, what lead me to believe I coudn't get sound at all. How, if at all, can I get sound to all my speakers in Rhythmbox?

I have a SoundBlaster Live! and Sigmatel STAC9708/11 according to alsamixer.

Thanx, I would be very grateful for your time and guidence.

---

### Post by endy on 2005-08-17
As most music is just two channels. Only my front two speakers give any output during playback of mp3s. I use beep-media-player for mp3s btw, but that shouldn't make any difference.

However, I have a contol box thingy that came with my speakers that will double the output to the rear speakers, if you don't have the same option on your speakers maybe there is a software plugin for Rhythmbox or setting somewhere that lets you do the same, or even perhaps something in alsamixer I'm not sure :S

Regarding 'LFE' according to [Wikipedia](http://en.wikipedia.org/wiki/LFE) it should be for your subwoofer, could it be your wires are mixed up?

Also you say that all the speaker volumes are set to 100% on alsamixer, I've noticed that sometimes for some cards somechannels have to be off or sometimes unobvious channels are actually balance or fade so it may be worth exploring alsamixer a little more.

Hope I've helped :)

---

### Post by TristanMike on 2005-08-17
Ok, thanks  :) , I need to keep Wikipedia in the back of my head, I'm still so very new, and any advice and info is helpful  ;-) . I hope I don't annoy people. I'm a Linux Virgin and Ubuntu is my first dive into the shall we say waters of computers. I just want my computer back from Microsoft.  

It's kinda confusing because Windows would give me the rear channels. Of course, when I ran the driver install it asked me how I wanted it and stuff, I'm sure Creative is more Microsoft friendly then Linux. Is that just the underlying issue here, Window's "fakes" the surround?  Or is it possible to achive that? that's all I'm really concerned about right now.

As for alsamixer, I'm fiddling with it, I know my fade is ok because I could here them in the sound test, so they're not too low, but if you(someone) could answer, I kinda feel dumb for asking...but do I need to refresh anything when making changes to the alsamixer.

---

### Post by TGDuff on 2005-08-19
I also have a Sound Blaster Live! (Sigmatel STAC9708/11) with 5.1 speakers that I am trying to configure.  The Left, Right, and Center channels (and I assume the LFE channel) are working via the sound-test command but I am not getting any sound from the rear speakers.  I would appreciate any tips on how I should configure my ALSA settings.

---

