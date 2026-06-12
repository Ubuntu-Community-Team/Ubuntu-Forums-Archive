---
title: "Audigy 2 AC3 Passthrough Issue"
date: 2005-07-19
forum: Hardware &amp; Laptops
---

### Post by oaaltone on 2005-07-19
I'm using mplayer to play a video with Dolby Digital (AC3) audio. I've successfully enabled AC3 passthrough with the "-ac hwac3," option in the mplayer config file. Everything seems to work: my receiver shows normal PCM input until mplayer begins playing a file with digital audio, then it switches to DD mode on the detection of the digital signal; all is normal.

The problem is this: after I close mplayer, the sound card continues to stay in digital mode, and the receiver doesn't switch back to PCM for "normal" audio to be heard. This is not the receiver's fault, because if I unplug the SPDIF input, it immediately changes back to normal; plug it back in and the card's still sending the digital signals. As a result, if I play a file with a digital audio stream, I have to power the computer off to gain "normal" audio abilities.

Is there some way to manually switch the Audigy 2 card back to "normal" mode?

---

