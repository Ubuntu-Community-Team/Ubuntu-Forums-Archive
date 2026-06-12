---
title: "Nvidia MCP51 Intel-HDA Sound crackly static. Seems like hardware trouble."
date: 2009-09-21
forum: Hardware
---

### Post by TheCelloFellow on 2009-09-21
Until the a few days ago the sound on my laptop worked perfectly (well, it didn't work at all in Gutsy but Hardy fixed that, but that's history). But three or four days ago (couldn't say which) the sound broke. I'm not sure if it's a hardware issue. The sound from the left channel, both from the built-in speaker and when using headphones, doesn't work at all. The sound from the right channel. is nothing but intermittent crackly sounds. This is when using ALSA, whether directly or via PulseAudio makes no difference.

The problem isn't only when using ALSA. If I use OSS the left speaker is muted except for intermittent bursts of sound. The right channel works mostly ok except it cuts out a bit sometimes.

I didn't fully notice this until now because I was using my USB Headset for most of my sound during the last few days cause I was doing some video editing. I wanted some decent sound and my headset sounds better than my built in speakers. I was aware that something was wrong but had no time to investigate.

This appears to have started doing this when I started using the realtime kernel and PulseAudio in realtime mode to facilitate the video editing I was doing. Cinelerra would for some reason crash PulseAudio when using the Esound audio output for Cinelerra unless Pulse was running realtime. That's the only thing I can think I did differently in that time. But while I was using this realtime PulseAudio and kernel, I wasn't using this particular onboard HDA soundcard, but my USB headset. Another thing that did occur is that Cinelerra's defaults are to use the OSS driver on /dev/dsp0, which may have caused some problems for my soundcard.

I'm very perplexed. Any hints, methods of testing my soundcard perhaps, or (you'll be a saint in my eyes) fixes are greatly appreciated.

-Josh

---

### Post by TheCelloFellow on 2009-09-22
bump

---

### Post by TheCelloFellow on 2009-09-25
Bump again

---

### Post by jchiso on 2009-12-12
Also afflicted with this noise issue. Any help would be appreciated...

---

