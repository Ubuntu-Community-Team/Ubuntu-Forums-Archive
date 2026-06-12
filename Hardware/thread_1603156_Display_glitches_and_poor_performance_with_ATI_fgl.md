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

### Post by keibee on 2010-10-30
bump   I have the same issue after upgrading from 10.04 to 10.10 running on ATI Radion mobility HD 4200 (Acer Aspire One 521).


Video performance, especially in full screen mode, is extremely bad.  
Removing fglrx breaks so many things... took me an hour to bring it back.

I urgently need some suggestions to get this solved, it drives me up the wall.


Keibee

---

### Post by PRC09 on 2010-10-30
This MAY be of interest or assistance.....I have used it on several machines and it does improve performance tho I wasnt having problems to start with....


[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

---

