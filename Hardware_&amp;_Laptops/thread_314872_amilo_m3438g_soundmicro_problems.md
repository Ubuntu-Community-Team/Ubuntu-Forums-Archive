---
title: "amilo m3438g sound/micro problems"
date: 2006-12-08
forum: Hardware &amp; Laptops
---

### Post by matzza on 2006-12-08
Hey Folks,
I've the problem that I can't get the internal microphone running in Ubuntu 6.06 using kernle 2.6.15-27-386. I realy tried everything to get that sh*** working, I've read much forums but I can't get a clear instruction or a solution for that prob. You guys are my last hope, maybe someone of you have a similar problem or an idea how to get that fixed?
Here is what I have done till now:
I've the Amilo M3438G NB. High Definition Audio is working wonderful, but not the internal microphone (used for skype ekiga-soft-phone and other communication tools). So I decided to update to the newest alsa-driver where the micro was deactivated by default after installation, which is ok, but after activating and testing the micro with an audio recording tool like audacity I couldn't hear anything, only if I knock on the micro and restart the playback I was able to hear the knocking very weak. So the micro is present and not defective. I tried to look for the "MicBoost" in the alsa-mixer... no success. I played a round with the "Capture devices" and switched several "Input Devices" from "Front Mic" to "Mic", "Line" "CD" etc and tested each config. but that doesn't seems to help. I'm going to get mad.. :evil: 
...fu*ng micro. I don't have an headset or an external Mic to test the LineIn.
Has someone a suggestion?
I appreciate every help, thanks.

---

### Post by SatanzJudge on 2007-11-16
I know it's been a while but I have the exact same problem :( Until now I was unable to get the mic working with Linux. I'm currently using Kubuntu 7.10 with Kernel 2.6.22. I suspect that the sound chip is still not fully supported by ALSA.

I you've found a working solution please let me know.

---

