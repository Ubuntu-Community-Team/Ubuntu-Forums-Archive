---
title: "Jaunty 64: Colors too dark &amp; strange mousepointer"
date: 2009-05-04
forum: Hardware
---

### Post by 10o on 2009-05-04
Two days ago I installed Jaunty 64 bits on a desktop with these specs:

Processor:AMD Athlon 64 X2 6000+
Motherboard: Asus M2A-VM HDMI
Graphics: ATI Radeon X1250 (integrated on motherboard)
Memory: 4GB
Screen 1: Samsung SyncMaster 206bw (20" 1680x1050)
Screen 2: IIyama (14" 1024x768)

Two problems occur:

1. All colors on the screens are too dark and 'colorful'. All of the standard monitor presets are too dark and even my custom settings with brightness set to the max and blue turned way back, colors are still not natural. This is a big problem for me since I work as webdesigner. I don't have a clue how things look on other monitors now...

In XP things look normal. In Hardy they used to too.

2. When moving the mousepointer over certain areas, e.g. menu's and buttons, it regularly starts blinking or some lines are 'dancing' around it.

I have tried adding radeonhd & xserver-xorg-video-radeonhd in Synaptic. And as soon as I add the line ```
Driver "radeonhd"
``` in the Device-section of xorg.conf, screens are not detected anymore and both have minimal resolution, so that does not seem to work.

I'd love to hear some more ideas.
Greetings from The Netherlands.

---

