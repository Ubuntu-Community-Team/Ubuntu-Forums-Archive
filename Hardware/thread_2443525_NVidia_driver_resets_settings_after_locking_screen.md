---
title: "NVidia driver resets settings after locking screen"
date: 2020-05-16
forum: Hardware
---

### Post by eltimablo on 2020-05-16
This is a bit of a weird one.

Whenever my screen locks and my monitors power off, nvidia-settings resets the checkboxes for ForceFullCompositionPipeline and AllowGSync back to some prior state that I can't seem to change. This didn't happen in 18.04, but it did happen in 19.10 and is continuing to happen in 20.04. I have an RTX 2070 Super.

Things I've tried include changing the settings as root and making a new user and seeing if the problem persists there (the answer is "sort of" in that it resets to a different set of settings). I've also saved the settings to my xorg.conf, which gets them to apply immediately after a reboot, but they're lost as soon as the screens power off.

As of right now I have an alias that I run which sets the metamodes for me, but that's tedious to run every time I log back into my computer.

Additionally, I've been getting an error in nvidia-settings when I try to exit where it asks if I want to apply my settings, even if I've already applied them and the button is greyed out. I think the two issues might be related, but I can't prove it.

---

