---
title: "Synaptic touchpad disable by default"
date: 2007-01-11
forum: Hardware &amp; Laptops
---

### Post by ukch on 2007-01-11
Hi,

I'm using an Acer laptop with a USB mouse and a touchpad. When the touchpad is enabled, pressing fn-F7 on my keyboard disables the touchpad, then pressing it again enables it. Since I have a real mouse I usually switch the touchpad off when I start using my computer, but often I forget, leave it on and accidentally click it somewhere stupid, so I would like it to be disabled by default.

When searching through the forums for an answer, I came across a thread that suggested I add the line
```
Option          "SendCoreEvents"        "false"
```
under the 'Synaptics Touchpad' section of my xorg.conf. I tried this, and lo and behold my touchpad stopped working. However, when trying to switch it back on using fn-f7, I found that the key combination didn't work any more.

Never one to give up after the first hurdle, I decided to try something else, so I had another look and came across a thread that suggested I add the line
```
Option          "SHMConfig"             "on"
```
to my xorg.conf and I try the command
```
synclient TouchpadOff=1
```
So I tried the command, and my touchpad switched off like a charm, but the only way to get it to work again was to negate the synclient command. Pressing fn-f7 had no effect.

My question is this: Is there any way to have the touchpad disabled by default, but enabled when I press the right key combination? How exactly does Ubuntu handle that anyway, if it doesn't use synclient?

---

