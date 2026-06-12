---
title: "Volume control issues with Master, PCM, &amp; LFE channels"
date: 2009-04-12
forum: Hardware
---

### Post by phenest on 2009-04-12
I have a Dell laptop that has 2 front facing speakers and a sub-woofer underneath. The 2 front speakers are controlled by the Master channel, and the sub-woofer is controlled by the LFE channel. I have set the PCM channel to be used as the main volume control so the Master and LFE can be left at maximum. This works quite well except for a couple of things:

1. If I mute the volume, I get a crackling sound (PulseAudio issue). This only happens when muting PCM, and doesn't happen with the Master or LFE. But seeing as I'm using the PCM to control both Master & LFE, this is a bit annoying.

2. Although using PCM for volume control works ok, as the volume gets lower, the sub-woofer can sound louder than the other 2 speakers, and at low volumes still sounds fairly loud. I think a better way would be if the LFE channel changed with the PCM channel, which would give a quieter volume.

Has anyone any suggestions?

---

### Post by phenest on 2009-04-12
Hah! Well I'll be damned! No sooner had I asked the question, I discovered I can set more than one channel for volume control. So I've set all 3 channels for volume control and now I can achieve a quieter volume, and the mute issue has vanished.

Oh, well. If any one else has this problem, now has the answer.

---

