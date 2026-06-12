---
title: "Trouble with Lubuntu and Jack (with Catia)"
date: 2017-11-03
forum: Hardware
---

### Post by brandflakemario1 on 2017-11-03
Hello everyone!

I am currently trying to route audio from Catia (I installed all of kxstudios repository) and I cannot get alsa to output sound with jack running at a sample rate of 96000hz. The only two sample rates that work in jack are 44100hz and 48000hz, although 48000hz seems to have artifacts in the audio (glassy sounds). Is there any way to force alsa to use 96000hz? I can get and meter audio from jack and Catia, but this audio won't send to playback (and I figure alsa is what is being used for jack to communicate with my hardware).

---

