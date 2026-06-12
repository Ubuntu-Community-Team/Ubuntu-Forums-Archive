---
title: "HDMI sound gone on kernel upgrade"
date: 2009-08-24
forum: Installation &amp; Upgrades
---

### Post by ThndrClsp on 2009-08-24
Hello,

Pretty new to Ubuntu, so unsure what to do with this problem.

One of the more recent upgrades recently sent in the update manager has been the kernel update.  However, I am unable to use the new kernels because my sound  literally disappears:

2.6.28-13-generic

w@w-HTPC:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

2.6.28-15-generic

w@w-HTPC:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Does anyone have an idea where I should start to get the HDMI connection back?  Using Jaunty, ALSA 1.0.20, and basic sound on motherboard (Intel G45.)  (Any other info you need, just ask.)

Thank you,

Wood.

---

### Post by junke1990 on 2009-08-24
in terminal open **alsamixer** and check if everything is open

---

### Post by ThndrClsp on 2009-08-24
> **junke1990 said:**
> in terminal open **alsamixer** and check if everything is open

alsamixer is fine.  All items are checked, but still the HDMI hw (0,3) is gone.

---

### Post by junke1990 on 2009-08-24
had probs myself too it helped to reinstall alsa.

walk trough the guide [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) it usually helps me.

---

### Post by ThndrClsp on 2009-08-24
> **junke1990 said:**
> had probs myself too it helped to reinstall alsa.

...

Junke,

Thank you.  Did a reinstall of alsa, and my sound restored.

---

