---
title: "PulseAudio Volume Mapping to Bass/Treble?"
date: 2009-09-29
forum: Hardware
---

### Post by kylemallory on 2009-09-29
I'm not sure entirely what is going on with my laptop (Dell Precision M90), but after upgrading to the Karmic pre-releases, I'm noticing that my volume media keys on the front of the laptop, change what seems to be the bass or treble settings for the internal sound card, rather than the volume itself.  The notify says its changing the volume, but the volume is consistantly loud, however the dynamic of the sound changes from full-volume sounds rich, to 10% volume sounding very bassy.  Ironically, when the volume goes to 0% (mute) the sound is actually muted.

Anyone else seen this?  Does anyone have any ideas on how to correct it?  Possibly a configuration setting somewhere?

I've looked into all the pulse-audio utils, but none of them proved very helpful.

Thanks,

---

### Post by kylemallory on 2009-09-29
Turns out, the volume control is not affecting the LFE levels in the ALSA mixer (it is, but not as it should be).  I'm curious if others are seeing a similar issue.  I made a video and reported to the PulseAudio mailing list.

[http://www.vimeo.com/6825531](http://www.vimeo.com/6825531)

---

