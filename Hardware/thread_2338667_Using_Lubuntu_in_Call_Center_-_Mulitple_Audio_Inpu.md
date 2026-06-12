---
title: "Using Lubuntu in Call Center - Mulitple Audio Inputs/Outputs"
date: 2016-09-30
forum: Hardware
---

### Post by sedwardspwna on 2016-09-30
I'm new to Linux and looking at running Lubuntu in a call center environment.  We've got about 100 intel NUC's (NUC5CPYH) that work well in Windows, but when trying out a different dialing platform thats browser based it lags.  Running the new browser based dialer in Lubuntu works like a charm, but whenever we change out the USB Headphones the audio quits working at the OS level.  A reboot gets it working again, but I'm wondering if there's a way to make it default to any headphone without requiring a reboot.

We're using PulseAudio as the sound control.

---

### Post by DuckHook on 2016-09-30
*Thread moved to **Hardware** as the more appropriate forum.*

Welcome to the forums sedwardspwna,

I realize that you are new to Lubuntu, but moved your thread to the HW forum because it is a better fit to the question you are asking.

Audio is pretty basic to the operation of the OS, so it gets initialized very early in the boot process. USB in particular is also built into the kernel (not an external driver process) so cannot be cycled or reset through a simple physical unplug/replug process. Yanking out the headphones may be akin to an unexpected amputation as far as the kernel is concerned. It may handle the sudden loss with some degree of elegance&#8213;in that it doesn't go into full panic&#8213;but asking it to handle the subsequent grafting of a new limb with similar elegance could be asking too much.

I'm neither a kernel nor USB expert, so I hope more knowledgeable people will chime in here.

---

