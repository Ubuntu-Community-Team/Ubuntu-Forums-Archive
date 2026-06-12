---
title: "Display glitches and poor performance with ATI fglrx driver on ThinkPad X100e"
date: 2010-10-22
forum: Hardware
---

### Post by rewbs on 2010-10-22
Hi all,

I noticed that video performance on my Thinkpad X100e was very poor compared to Windows 7, so I installed the ATI fglrx proprietary drivers by using the "Additional Drivers" dialogue box. The system has an ATI Radeon Mobility HD 3200 chip.

The result of installing the drivers is pretty devastatingly negative, with symptoms such as skewed content in windows, browser tabs and text boxes failing to refresh when their content changes. In fact, please excuse typos in this post, because I can't really see what I am typing. :)

I also notice that HD video playback performance is no better - perhaps even worse - than prior to installing the drivers.

Example of what I see: [IMG]http://i.imgur.com/132Eu.png[/IMG]


Here's the output of **fglrxinfo**:
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 3200 Graphics 
OpenGL version string: 3.3.10237 Compatibility Profile Context
```

I'm on Ubuntu 10.10 with kernel 2.6.35-22-generic-pae. 

What can I try?

Many thanks,
-R

---

