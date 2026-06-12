---
title: "Non widescreen laptop + widescreen external monitor"
date: 2009-03-29
forum: Hardware
---

### Post by dave00 on 2009-03-29
Hi!

First of all, sorry about my bad English.

I wanted to use my Samsung widescreen monitor as an external monitor for my century old non-wide asus laptop. I do not wanted to set-up it as a second.

So my wishes:
If i plug the external LCD in i use it only with external keyboard and mouse but these don't matters.
If not, then i would like to use the laptop built in LCD.

I searched the net and added the following lines to the xorg.conf:

Option          "MonitorLayout" "CRT,LFP"
Option          "Clone" "true"

(Thanks Brian Pontarelli!)

Now i can see the desktop on my external monitor but i can not change the resolution of it.

**So i would like to use the external monitor with its native resolution(1650*1050) and the laptop with 1450*1050.**

Is this possible? What else should i add to the config file?

Thank you!

---

