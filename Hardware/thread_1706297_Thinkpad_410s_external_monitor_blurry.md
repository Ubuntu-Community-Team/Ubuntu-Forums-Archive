---
title: "Thinkpad 410s external monitor blurry"
date: 2011-03-13
forum: Hardware
---

### Post by Jengu on 2011-03-13
Whenever I plug my laptop into an external monitor (VGA cable) the display on the external monitor looks very blurry. What should be straight lines seem to be constantly 'dancing'. Under Windows 7 on the same machine it works fine. It doesn't matter whether the external monitor is mirroring or acting as a secondary display, still fuzzy.

The laptop comes with nvidia optimus (hybrid nvidia/intel) but I've disabled the nvidia chip in the BIOS settings, so I'm pretty sure this should be an intel driver issue. I've tried different VGA cables, but they don't make any difference either. I also tried upgrading to the git intel drivers from [this repo]("https://launchpad.net/~glasen/+archive/intel-driver") but they have the same problem.

I tried checking /etc/X11/xorg.conf, but it doesn't appear to exist in Maverick. I also went into the display settings and saw that it said the monitor refresh rate was 60hz and 1980x1020 resolution, just like it should. So I'm out of ideas. Any suggestions?

---

### Post by josvanr on 2011-04-06
I have the exact same problem on samsung SF310 and kubuntu 10.10. Have you managed to solve this?

josvanr

---

### Post by Jengu on 2011-04-06
I've managed to work around the problem for now by buying a display port -> VGA adapter. The video coming through that is almost perfect, except for every couple minutes or so it will garble for a second, but that's much more tolerable. I also opened a bug here, if you want to leave your hardware info: [https://bugs.launchpad.net/bugs/734487](https://bugs.launchpad.net/bugs/734487)

---

### Post by josvanr on 2011-04-09
hi  , thnx a good workaround.. I think the bug has been noted elswhere, with my hardware info given also....

josvanr

---

### Post by jonsson on 2011-05-13
Just came across this by googling... I have similar problems with my Samsung NF310 netbook (running Kubuntu Natty) with intel graphics. My external monitor looks blurry, even though it looks great when plugged it into my Dell laptop. :|

---

