---
title: "Two sound cards working, one with issues"
date: 2010-08-14
forum: Hardware
---

### Post by akuda on 2010-08-14
Hi,

I have a ThinkPad W500 with on-board soundcard, and an Audigy 2 ZS. Both work just fine with Rythmbox and Firefox, but only the on-board one works with games, like:
UT 2004, Heroes 3 (native), Majesty (native).

Any clue why?

Regards,
akuda

---

### Post by ratcheer on 2010-08-14
Maybe you need to make sure the Audigy is detected first by the system.

You can determine which one is detected first in several ways. I just use tha alsamixer command. When alsamixer starts, it defaults to showing the first soundcard. If it is your onboard card, you probably need to force it to second.

Tim

---

### Post by lepusfelix on 2011-01-28
I have a SB Live card that seems to work just fine. However, it's the onboard AC97 that is detected and configured, but just doesn't output at all. Alsa mixer shows it as the first one, and it also appears in the sound preferences as hardware. As far as I know, there should be no reson why it doesn't output.

---

### Post by towheedm on 2011-01-28
> **lepusfelix said:**
> I have a SB Live card that seems to work just fine. However, it's the onboard AC97 that is detected and configured, but just doesn't output at all. Alsa mixer shows it as the first one, and it also appears in the sound preferences as hardware. As far as I know, there should be no reson why it doesn't output.

Are you using PulseAudio?  It sounds as though the SB card is set as the default source in PA.

---

