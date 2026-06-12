---
title: "PC hangs hard with i915 driver?"
date: 2018-09-23
forum: Hardware
---

### Post by palteater on 2018-09-23
Hello. 

I have a HTPC running Ubuntu since a few years - I think I first installed 14.04, and then I have gradually upgraded as new versions came out. Currently running 18.04.

It crashes, randomly and hard. Garbled screen. No response, no switch terminals, no SSH. While doing things or while idling. No sleep state deployed, ever. When the TV is on, the sound also sometimes freezes and makes either a screecing noise or repeats the last fraction-of-a-second sound it played. Sometimes it's just silent. If it crashed when the TV was off, there is never any noise. Could it be HDMI related?

It crashes once a month or thrice a day - I see no pattern. It has always been like this - I remember it from way back, but I think it has possibly increased in frequency lately.

RAM passes tests without error. CPU is a non-overclocked Intel Pentium G3258 at stock speed. Temps are low. Tried underclocking it, no difference. PSU is adequate.

My other PC is a i5-3570. It is rock stable running Ubuntu 18.04. Considering that it has pretty much the same circuits and that the main difference is that it has a discrete nVidia card rather than integrated graphics, I naturally suspect the Intel graphics drivers. Googling around, I do also find a few other people that seem to report about the same error using i915 drivers, which confirms my suspicions.

Now - pray tell, how do I bug-search this? The crashes leave no traces in /var/log/syslog as far as I can tell. The last entries there are ususally something completely unrelated, when I go down the path of looking those up it ends with a "nah, this can't be it". So I suspect that the rig is just locking abruptly without writing anything there.

I'd slap a cheap nVidia card into that rig and be done with it, but there is no room for it. It's a tiny breadbox thing. I rather hope that there is some flag I can switch that disables whatever b0rks the system.

Thank you for any aid.

---

