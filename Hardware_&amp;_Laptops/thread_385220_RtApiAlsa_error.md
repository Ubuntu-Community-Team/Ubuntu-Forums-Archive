---
title: "RtApiAlsa error"
date: 2007-03-15
forum: Hardware &amp; Laptops
---

### Post by mariusthart on 2007-03-15
On my new Acer Aspire WLMi5102 laptop I get an error when I run a PyEPL experiment which is a Python library for doing behavioral psychology experiments.

The error is: "RtApiAlsa: callback thread error (RtApiAlsa: audio read error for device (hw:SB,0): Input/output error.) ... closing thread."

I don't know if this OS related or that it has something to do with the Python library. For the rest sound seems to work fine. But I did notice some other problems with sound on my type of laptop, which have all been solved as far as I can tell.

Does anybody have an idea what to do?

Here is my post on the PyEPL forum:
[http://sourceforge.net/forum/forum.php?thread_id=1692641&forum_id=548620](http://sourceforge.net/forum/forum.php?thread_id=1692641&forum_id=548620)

---

### Post by mariusthart on 2007-03-19
I have played around with using other sound devices in the 'Sound' item under Preferences and I get a different error now. Perhaps this makes more sense to some of you: 
 
ALSA lib pcm_dmix.c:862: (snd_pcm_dmix_open) unable to open slave 
The only available device does not support 2 channel full duplex! 
No default output device with correct channel info was found! 
You will not be able to play sound. 
 
RtApiAlsa: callback thread error (RtApiAlsa: audio read error for device (hw:SB,0): Input/output error.) ... closing thread. 
 
I have tried ALC883 Analog for all devices as well as ALSA and ALSA for all devices except for sound capture under audio conferencing (because the first error mentioned an audio READ error). This makes no difference at all. Disabling Software Sound Mixing also has no effect. 
 
When I try pushing the Sound playback Test button ALC883, OSS and ALSA produce an error: 
 
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Resource busy or not available. 
 
ESD and autodetect give a nice little window called: 'Testing pipeline' with a progress indicator, but there is no sound (which should be a beep with a frequency of 512 Hz I guess).

I thought all the issues with this card had been resolved, or am I wrong? And why do I get sound even though I can't test it?

---

