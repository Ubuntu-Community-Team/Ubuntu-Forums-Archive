---
title: "Replaced sound card, OSS trying to use old device."
date: 2008-12-13
forum: Installation &amp; Upgrades
---

### Post by triften on 2008-12-13
So my mother board has on board Intel HD Audio and I wanted to use a mic input. I discovered that there seem to be a few bugs regarding mic input, specifically, no Mic Boost option, so I tried installing the latest ALSA. That didn't fix it either.

So I installed an old SB Live PCI (emu10k1) sound card and disabled the onboard audio. I recompiled the alsa drivers, lib, and utils, but under the Alsa Mixer device selection, it lists "Sigmatel STAC9721,23 (OSS Mixer)". Also, "Preferences" lists options and channels that were on the onboard audio. Needless to say, adjusting these options makes things a little screwy.

How can I clear out the old options and devices? Is there a way to clear out all sound then let ubuntu automatically install the emu10k1 drivers and mixer configuration?

Thanks,
Triften

---

### Post by tommcd on 2008-12-14
Nere is a good howw-to that may help:
[http://ubuntuforums.org/showthread.php?t=922860&highlight=sound+cards](http://ubuntuforums.org/showthread.php?t=922860&highlight=sound+cards)

And welcome to the Ubuntu forums!

---

