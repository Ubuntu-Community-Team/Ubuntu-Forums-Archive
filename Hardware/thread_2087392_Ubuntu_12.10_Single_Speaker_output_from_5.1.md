---
title: "Ubuntu 12.10 Single Speaker output from 5.1"
date: 2012-11-23
forum: Hardware
---

### Post by dmouck on 2012-11-23
Hi folks,

I've looked around online and haven't found any solutions to this, I was hoping the community could lend a hand.

I am running Ubuntu 12.10 x64 with the hopes of ditching Windows 7 as my HTPC. Everything is working correctly except for the sound. My sound card is an Envy24PT/HT (VT1720/24). When I go to the sound settings in Ubuntu, my choices are:
HDMI / DisplayPort 2
Speakers (build-in audio)
Digital Output (S/PDIF)
Analog Output / No Amplifier VT1720/24 [Envy24PT/HT]
Analog Output / Amplifier VT1720/24 [Envy24PT/HT]

I have 5 speakers and a subwoofer setup (5.1). No matter if I select Analog Stereo Output or Analog Surround 5.1 Output, only the front-right speaker works on the test. Oddly enough, when I play music through Clementine, I can hear the subwoofer as well.

I checked alsamixer and selected the right sound card (Chaintech AV-710) and ensured that it is not muted (Master, PCM, Surround, Center and LFE are all unmuted). 

Please let me know what other information you need to troubleshoot this. I would prefer to not use audio from my HDMI as I would like to use that solely for video.

Thanks!

---

### Post by dmouck on 2012-11-24
I have some further feedback. In XBMC I have sound from the front-left and front-right speakers. This is bizarre; any thoughts?

---

### Post by dmouck on 2012-11-25
Okay nevermind, the issue appears to be faulty cables.

---

