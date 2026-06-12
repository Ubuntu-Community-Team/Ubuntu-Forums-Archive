---
title: "Where to find Synaptics Touchpad Drivers"
date: 2013-08-13
forum: Hardware
---

### Post by VegasTamborini on 2013-08-13
Alright, so I had a few problems installing Ubuntu on my laptop (Toshiba Satellite C875D) and posted a question in 'Installation & Upgrades', you can read all about it [here]("http://ubuntuforums.org/showthread.php?t=2166568"). Basically, the touchpad, keyboard, display and wireless weren't working. I have fixed the wireless, display, and for the most part the keyboard, however the touchpad is completely non-responsive and the keyboard still cuts out.
So, it's become less of a installation problem and more of a hardware/drivers issue, so I thought I'd repost here and see what happened.

As far as I can tell I need drivers for the following:

Touchpad:      SynPS/2 Synaptics TouchPad
Keyboard:      AT Translated Set 2 keyboard

I found a post that recommended I run:
[COLOR=#000000]```
 sudo apt-get install xserver-xorg-input-synaptics 
```

However the output for that is:

[/COLOR]```

xserver-xorg-input-synaptics is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```[COLOR=#000000]

I have also used the software updater and run the ```
sudo apt-get update
``` command, but no luck.

I am running out of ideas and would value any input.
[/COLOR]

---

### Post by DeanoCYM on 2013-08-13
Sound too simple but it happened to me before...

Have you got one of those function buttons on your keyboard that enables/disables the touchpad?

---

### Post by VegasTamborini on 2013-08-14
Haha, yeah, I've been caught out by that for an embarrassingly long time before too! However the problem seems to have stopped, Maybe it just needed to restart after sudo apt-get update.
Thanks for the help though

---

