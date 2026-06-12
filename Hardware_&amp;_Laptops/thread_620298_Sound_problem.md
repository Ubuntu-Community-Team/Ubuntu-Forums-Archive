---
title: "Sound problem"
date: 2007-11-22
forum: Hardware &amp; Laptops
---

### Post by c0xy on 2007-11-22
Hi,

Sorry if this is a silly question but one of the things holding me back from using Linux in general is that I've never been able to get the sound working properly. I have an Auzentech X-plosion sound card.

What ever drivers I try and use (OSS and ALSA) seem to give me sound but it is really 'skippy'. Sometimes it will work fine for a little bit but then I'll close the sound app and it will go crazy or it will start off fine and then go 'skippy' and then catch up with itself and be fine for abit.

Not sure if that makes sense but really want to start using Linux abit more but if I can't listen to music then that isn't going to happen!

Thanks in advance,
Paul

---

### Post by luciferin on 2007-11-26
Hi, I can try to give you a hand..  I just got this exact sound card in today and have it working perfectly.  I'm using ALSA with the default driver (CMI8770) and so far have no issues.  I have only tried the optical out so far but it works with DTS/DD passthrough and with digital PCM output.  There is no lag, no stuttering.  

Are you using the analog 7.1 outputs?  Does this stuttering occur on all playback or only on multichannel audio?

---

### Post by c0xy on 2007-11-27
Didn't even realise the Optical output worked on Linux! Did you have to do anything extra to set that up?

I seem to have narrowed the problem down to running Amarok with ALSA driver, if I change the driver to OSS in the Xine engine without Amarok it seems to work fine. 

Thanks,
Paul

---

