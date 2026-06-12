---
title: "Asus EeePC 900HD: lack of performance"
date: 2009-09-20
forum: Hardware
---

### Post by Triggonaut on 2009-09-20
...this thing is really getting on my nerves, as it keeps me awake for days and [my thread in the German forum]("http://forum.ubuntuusers.de/topic/asus-eeepc-900hd-cpu-bei-primitivsten-program/#post-2153369") gets no attraction or they're all way too shy to answer. :-)

The problem is, my netbook (Asus EeePC 900HD) running Ubuntu 9.04 cannot even do simple things as playing a youtube video without having the CPU under full load...

Have a look at the output of "top" while only running Firefox with one YouTube-tab:

```
top - 21:30:26 up 14 min,  2 users,  load average: 1.46, 1.31, 0.79
Tasks: 135 total,   2 running, 133 sleeping,   0 stopped,   0 zombie
Cpu(s): 89.4%us, 10.3%sy,  0.0%ni,  0.0%id,  0.3%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1018156k total,   541880k used,   476276k free,    20456k buffers
Swap:   994992k total,        0k used,   994992k free,   278772k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 2709 foobar    20   0  445m 103m  31m R 96.3 10.4   9:10.59 firefox
 2148 foobar    20   0  156m 4748 3624 S  2.3  0.5   0:13.72 pulseaudio
 2302 foobar    20   0 47776  23m  15m S  0.7  2.3   0:04.38 gnome-panel
 1679 root      20   0  9112 3384 2784 S  0.3  0.3   0:00.46 gdm-binary
 1845 root      20   0 44120  13m 8692 S  0.3  1.4   0:35.60 Xorg
 2208 foobar    20   0 99272  10m 8060 S  0.3  1.0   0:02.35 gnome-settings-
 2917 foobar    20   0  2588 1172  884 R  0.3  0.1   0:00.25 top
    1 root      20   0  2696 1392 1060 S  0.0  0.1   0:01.36 init
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd
```I don't know why my netbook sucks that much but it shurely has nothing to do with an issue about flash or firefox, because totem playing a standard PAL video from my camcorder gets the CPU wasted that way, too.

I've already tried the "[**HOWTO: Jaunty Intel Graphics Performance Guide**]("http://ubuntuforums.org/showthread.php?t=1130582")" (safe/optimal), but after rebooting still everything was the same, so I reverted the changes.

So now, it's up to you, maybe you have an idea, my question is:

[LIST]
[*]What kind of bottleneck is it? (e. g. misconfigured graphics driver? wrong kernel?)
[/LIST]
Even if you don't have any clue, it would be great if you could tell me where to start troubleshooting. As the only thing I recognize is the high CPU load, I have no idea where to look at.

Ah, yeah - I'm running the i386-kernel (but the eeepc- and generic-kernels suck as well) and compiz is turned off (it obviously makes no difference if turned on or off).

---

### Post by hetx on 2009-09-20
First I can suggest upgrading your kernel. The latest ones agree much better with the EEE PCs.

A good way of doing this is trying Easy Peasy. It's Ubuntu-based with Netbook Remix default (easily switched off) and has the latest kernel.

Easy Peasy also includes the Intel Graphics tweaks and UXA-something 3D graphics.

Not trying to sell it, just saying it could be what you need =D I run it on my 900A, works great.

---

### Post by Triggonaut on 2009-09-21
Hmm, maybe that would be the best solution with Easy Peasy, I agree...

But it would be even better for me to find a solution without re-installing my system, that reminds me a little to the earlier days of MS Windows... :)

I will try some UXA / EXA configurations tonight, maybe that helps.
Further comments are highly appreciated. :)

---

### Post by blackened on 2009-09-21
The regressions in the Intel driver in Jaunty are just horrible. I wound up ditching Ubuntu on my EEE because of it (that and my absolute inability to leave well enough alone).

If it were me, I would revert back to Intrepid until the problems are officially fixed.

---

