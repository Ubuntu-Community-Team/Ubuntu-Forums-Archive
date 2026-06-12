---
title: "External Soundcard fully working with Ubuntu"
date: 2014-06-14
forum: Hardware
---

### Post by troffasky on 2014-06-14
> **gtippitt said:**
> Even though this is an old message, I am posting this reply in case others are still looking for a solution with 5.1 on the Extigy. I had a Creative Sound Blaster Extigy USB sound adapter that worked great with Ubuntu before PulseAudio, but has not worked with 5.1 since PulseAudio. The Extigy worked with OSS, but not with PulseAudio. 

I found this also - optical out was lit up until connected to PC - strange, eh? The fix to this: open alsamixer in a terminal. If you see only a single channel, press F6, select 'Sound Blaster Extigy', press enter, you should then see a load of channels. Press right arrow until you get to 'S/PDIF Optical'. Press 'm' to unmute it. Optical out will light up. Job done!

---

