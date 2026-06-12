---
title: "[dri] DRI working, but still slow"
date: 2004-12-26
forum: General Help
---

### Post by LB06 on 2004-12-26
Hello, I've been running Warty for a couple of days, but I cannot get my opengl working properly. glxinfo reports direct rendering: yes and I the correct modules are properly initialised by hotplug (intel_agp, i830, agpgart). And /dev/dri/card0 has the right permissions.

Glxgears however gives me only ~300fps and tuxracer and other GL games run pathetic. The only errors I can find are in my xfree logs:
```

drmOpenDevice: minor is 0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (Unknown error 999)
drmOpenDevice: open result is -1, (Unknown error 999)
drmOpenDevice: Open failed
drmOpenDevice: minor is 0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (Unknown error 999)
drmOpenDevice: open result is -1, (Unknown error 999)
drmOpenDevice: Open failed

```

A few lines futher however, it says everything's ok:
```

drmOpenDevice: minor is 0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenDevice: minor is 0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenDevice: minor is 0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmGetBusid returned ''
(II) I810(0): [drm] created "i830" driver at busid "PCI:0:2:0"

```
dmesg doesn't report anything unusual.

I have an Intel I855GM IGP graphics card and a intel pentium M715 Dothan. My previous distro's (most notably Arch and Slack) could run glxgears @ 700fps and tuxracer at high speed. At first I thought it was just that the i830 drivers wasn't fast enough, but after a checkup I found out that in Slackware 10 I was also using the i830 driver instead of the new i915 driver, so I don't believe this is the problem.

Any help would be appreciated. Thanks in advance :)

---

### Post by clsdaniel on 2005-01-02
That's weird, i have the same graphics card on my laptop, which is a celeron by the way, and everything runs fine, the difference i see is that your config is loading the i810 dri driver, while on mine it loads the i915.

Tuxracer runs fine out of the box and glxgears gives around 348 fps.

I will try the i810 driver to see if gives better or worst results.

Good Luck.

---

### Post by LB06 on 2005-01-02
The i915 DRI driver is only available for linux 2.6.9 or higher (Hoary). Btw I am running the i830 driver. The i810 driver is my X driver, which you must be using too I guess.

---

