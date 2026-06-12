---
title: "Scratchy Audio on HP Laptop"
date: 2008-11-16
forum: Hardware
---

### Post by codyhendrix2 on 2008-11-16
I am running Ubuntu Studio 1.9 on an HP Pavillion DV5-1002nr. I have had quiet, intelligible, scratchy audio since I updated or rebooted for the first time.. not sure which caused it. I have an Intel IDT HD sound card. After going through the sound settings and testing all of the different options I found that I have to have it on the HDA ATI SB (Alsa mixer) device setting with the PCM volume up for the sound to actually work (the PCM volume is down/off by default). Most of the other device options would play the test tone fine when I clicked "test" but would still play static for everything else, flash, AVI's, MP3's etc. That being said, after I reboot my machine the HDA ATI SB setting is still default but I get static right off the bat but as soon as I move the PCM fader in the mixer up even a little it clears up and returns to normal. So I guess my question is this... How do I set the default mixer settings and volume levels so I don't have to go through this procedure every time I reboot? I've never had any sound issues with any other ubuntu distro but I settled on this one because its the only distro on which I could set up CPU frequency scaling without getting an "Access Denied...CPU Scaling Unsupported" error. The other distros were causing my CPU to burn up!!! This sound issue is about the only thing standing between me and a fully functional self sustaining distro. Thanks in advance for any info!!!

:guitar::guitar::guitar:

---

