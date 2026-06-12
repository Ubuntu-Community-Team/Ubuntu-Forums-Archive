---
title: "Creative X-Fi extreme audio notebook in 8.04"
date: 2008-06-17
forum: Hardware
---

### Post by s0ury on 2008-06-17
Greetings. I'm a fairly new Linux user, and Ubuntu is the first distro I've installed, 8 months ago.

For 8 months I've been trying to make my audio card work, and currently it is the only reason I have Windows installed. I use my audio card to output digital sound to my 5.1speakers since I use my laptop to watch DVDs.

The sound card is the Creative X-Fi Extreme audio notebook, PCMCIA.

My lspci | grep Creative output is:
```

04:00.0 PCI bridge: Creative Labs Unknown device 7006
05:00.0 Audio device: Creative Labs [SB X-Fi Xtreme Audio] CA0110-IBG

```
I don't seem to be able to find this device in the Sound options.
I would also like to say that I have installed the latest ALSA build from their website (version 1.0.17rc2), before I didn't get anything related to "Creative" in lspci (or at least I didn't in 64-bit, i just fresh installed 32-bit 8.04)

I had tried to install OSS on gutsy 64-bit but it corrupted my mic, so instead of trying to bring ALSA back I fresh-installed 8.04.

Any help welcome :)

PS: The xtreme audio notebook chip is not an X-Fi chip, it is a repackaged SB Live!24, or so ALSA says.

---

### Post by rofthorax on 2008-10-06
Just relaized that one of the messages was on a "read only archive"... Why?

Anyhow, here is a link to the specific laptop card described here it seems, and hopefully will raise awareness of what Creative has available.. No this is not yet another X-fi sound conditioner, but in fact is a X-fi card.. 

[Creative X-fi Laptop Card]("http://us.creative.com/products/product.asp?category=209&subcategory=669&product=17988")

My bad.. Yes it is, nowhere in the ad does it say it is a sound card, it only talks about augmenting your audio.. Great, Creative is yet again trying to make money on the hype surrounding the "X-fi" soundcard. BTW, I have the X-fi soundcard and it is actually worse than the Soundblaster Live!'s ont he windows platform as the control panel has been dumbed down for idiot consumers. The Live! offered the ability to use hardware (DSP programmed) filters that performed effects like pitch shifting, reverb, room delays, flanging, etc.. Many feeding back into each other.. Also supports things like "What You Hear" where what is recorded is what comes out of the soundcard.. 

Linux desperately needs something like that..

---

