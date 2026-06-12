---
title: "RadeonHD 7750, no window dropshadows in unity"
date: 2013-11-06
forum: Hardware
---

### Post by rachel.greenham on 2013-11-06
Actually I'm pretty pleased with this. After all the scare stories I'd heard about AMD cards on Linux, but wanting a card that would drive 3+ monitors for less than a milspec budget, I finally went ahead with more optimism than sense and bought one: a Radeon HD7750 with four mini-displayports... and after getting my previous nVidia configuration properly out of the way (uninstalling nvidia drivers is necessary to select the correct libGL in update-alternatives, and don't have nomodeset in your kernel params), it all Just Worked on the open source radeon driver, which makes me happy. I hear terrifying stories about catalyst.

OTOH feeling slightly cheated out of a few distracting days fiddling with it to get it to work...

ie:

```

rachel@twilight:~$ glxgears -info
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
GL_RENDERER   = Gallium 0.4 on AMD CAPE VERDE
GL_VERSION    = 2.1 Mesa 9.2.1
GL_VENDOR     = X.Org

```

I think that's using the card's 3D, not llvmpipe isn't it? Certainly there's no discernible impact on CPU usage while running.

For once my timing was impeccable, because it seems full support for this only went in towards the end of the Saucy development process, which makes the section in [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) where it says 3D isn't supported for HD 7000 series out of date; but only just, and only for 13.10.

But, there's just one teensy-little thing, not enough on its own to make me install catalyst et al. The desktop effect of shadows around the windows has gone missing in action. I'm pretty sure this was working before (on nvidia) or I don't think I would have noticed the absence. According to ccsm the effect is on, but there are no shadows.

Everything else seems actually to be working fine. Active blur behind dash, active transparency behind launcher and terminal, the other usual compiz effects like the window-zoom of super-w.

So it's like something just turned it off, perhaps a leftover assumption that i should be on a lower graphics setting.

(One other thing. The fan on this thing is *noisy*. I think it out-noises the rest of the computer, even though it has six hard drives in it. sensors reports it's running between about +62.0°C and +67.0°C. Guessing I may be starting to need a side case fan. Or the computer gets banished to a cupboard. I didn't buy these 5m displayport cables for nuffink.)

(Actually... now I'm on an opensource driver, I guess xmir is in scope now. Although they didn't default it for saucy because of multi-monitor issues, and I *bought* the card to run 3 monitors on it, so that may be asking for trouble...)

---

