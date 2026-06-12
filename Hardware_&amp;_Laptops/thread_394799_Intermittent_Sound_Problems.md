---
title: "Intermittent Sound Problems"
date: 2007-03-27
forum: Hardware &amp; Laptops
---

### Post by BatteryKing on 2007-03-27
OS: Ubuntu 6.10 Edgy Eft
(Resolved: Upgrading to 7.04 resolved issue.)

Hardware of interest:
1. Computer: Gateway NX860XL Notebook
2. Processor: Core2 Duo
3. Sound: Built in Intel HDA sound (SigmaTel ID 7634 according to Ubuntu).

I almost have everything working on my notebook except for some intermittent initialization problems and special keys (which I don't really use anyway) crashing the X server.

The most annoying of the intermittent initialization problems which I am trying to tackle now is the sound initialization problem where about a quarter of the time the sound seems to initialize according to the logs and the sound mixer comes up, but no sound comes out irregardless of volume level, mute/unmute settings, and whether or not I am using the built in speakers or headphones (the switch over mechanism works fine).

So far I have noticed when the sound does work alsamixer detects only a "Master" channel and a "PCM" channel and when it does not work alsamixer detects an additional non-existent "SPDIF" channel giving you a "Master", "PCM", and "SPDIF" channels.

Any suggestions on how to fix this problem?

Update: As of installing the latest kernel patch (as of 2007-04-11) the problem has worsened to the sound failing to initialize properly three quarters of the time, now making this a very frustrating problem because I use the sound all of the time in Linux (or at least keep trying to).

Update: Upgraded to 7.04 and sound issues went away.  Actually there were several issues I was experiencing with 6.10 that seem to be resolved in 7.04.

---

