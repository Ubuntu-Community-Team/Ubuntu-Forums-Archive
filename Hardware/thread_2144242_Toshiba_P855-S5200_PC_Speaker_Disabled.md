---
title: "Toshiba P855-S5200 PC Speaker Disabled"
date: 2013-05-11
forum: Hardware
---

### Post by Zeklandia on 2013-05-11
The PC speaker (internal speaker) only works in the recovery kernel, even though pcspkr is loaded and not in the blacklist file. Neither ```
echo -e "\a"
``` nor ```
beep
``` will produce any noise unless I choose the option to drop into a root prompt in the recovery kernel, but all other audio works fine. I removed it from the blacklist file completely, and lsmod shows it as loaded, but it only works when booted into a recovery kernel and when given the list of recovery options, I drop into a root prompt. Then and only then do ```
echo -e "\a"
``` and ```
beep
``` produce sound output (really loud output I might add). I have a netbook that is also running 13.04 that has the beep enabled, and ALSA even shows the volume for it when I execute alsamixer in a terminal.

---

### Post by Zeklandia on 2013-05-12
Okay, I fixed the touchpad. Currently I am trying to repair an old Windows installation, so when I was booted into the Windows disc, I hit the function key and then the touchpad started working again, but it is odd that Windows can change that while Ubuntu and the BIOS have no control over it. I still can't get the beeping sound from the PC Speaker, but all other audio works fine, and the beep even works on my old netbook, which I did the same things to turn it on with.

EDIT: Oops.

---

