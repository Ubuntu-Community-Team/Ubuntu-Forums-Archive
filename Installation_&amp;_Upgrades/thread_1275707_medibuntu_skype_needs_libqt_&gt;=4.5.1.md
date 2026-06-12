---
title: "medibuntu skype needs libqt &gt;=4.5.1"
date: 2009-09-26
forum: Installation &amp; Upgrades
---

### Post by davidmaxwaterman on 2009-09-26
How to get qt >= 4.5.1 so I can install skype from medibuntu?

Max.
9.04

---

### Post by mikewhatever on 2009-09-26
That's very odd. I suggest you download Skype from here [http://www.skype.com/intl/en/download/skype/linux/choose/](http://www.skype.com/intl/en/download/skype/linux/choose/) and install it by simple double clicking. It only requires Qt 4.2.1+.

---

### Post by davidmaxwaterman on 2009-09-26
> **mikewhatever said:**
> That's very odd. I suggest you download Skype from here [http://www.skype.com/intl/en/download/skype/linux/choose/](http://www.skype.com/intl/en/download/skype/linux/choose/) and install it by simple double clicking. It only requires Qt 4.2.1+.

Yeah, I've since done that, but it would be good to have a solution that is easier to maintain. Of course, easy to install is important too :)

I noticed on my previous installation that Qt 4.6 breaks Skype due some missing symbol - I forget what it was.

I now have an issue with it not being able to use my webcam's microphone. If I select it in 'Sound capture' on the desktop's System/Sound 'Sound Preferences' tool, and use 'Test', it works just fine - it's USB Device 0x46d:0x8b1 USB Audio (ALSA).

I'm really not clear on how the ALSA and PulseAudio are related, but I only have 'PulseAudio server (local)' in Skypes 'Sound Devices' panel. In my previous installation, I could select different devices there, so I'm not sure what's changed :/

At the moment, I'm making do with the mic in my laptop, since that seems to work ok.

Any ideas?

Max.

This post had the solution for my usb mic : <[http://forum.skype.com/index.php?s=&showtopic=411431&view=findpost&p=1886151]("http://forum.skype.com/index.php?s=&showtopic=411431&view=findpost&p=1886151")>

---

