---
title: "Touchpad Settings - Disable move when tapping?"
date: 2013-05-16
forum: Hardware
---

### Post by Roasted on 2013-05-16
I noticed in Ubuntu 13.04 whenever I change the touchpad settings within system settings, they don't stick. A buddy confirmed this on a different laptop (once you close and go back in the sliders are back to default). Anyway, I'm resorting to synclient to see if there's a way to work around this issue. On my laptop I'm having issues with the tap to select. Whenever I tap the touchpad to select something, the cursor will move. The thing is, the act of the cursor moving often moves far enough away from my target. I've tinkered with a bunch of synclient settings but nothing really stuck out. I adjusted my FingerHigh to 45, which for this touchpad felt much better than 25 but still not quite a home run. I tinkered with some other settings but, eh, nothing quite yet.

I figured I'd ask here to see if anybody else knows of a specific parameter that will undoubtedly tweak the behavior I'm looking to curb. Like I said, I'm just looking for a way to disable the cursor from moving when I tap on the touchpad.

Thanks!

---

### Post by royer10r on 2013-06-14
I am having the same issue as well. everything else is working good enough i just can;t stand tapping on something and having the pointer move and end up clicking something else.

Dell XPS 14 Ultrabook.

I have tried installing the synaptics package from the software center and running it via the command line to set it up but it doesn't help. I would love a solution as well.

---

### Post by royer10r on 2013-06-14
i did some more digging and i found this package gpointing-device-settings .
it seems to work but i still need to find that sweet spot in the settings. it has options to adjust 'tapping time', 'tapping move', and a check box to enable faster tapping.
after installing just open the terminal and launch it manually 'gpointing-device-settings'

---

