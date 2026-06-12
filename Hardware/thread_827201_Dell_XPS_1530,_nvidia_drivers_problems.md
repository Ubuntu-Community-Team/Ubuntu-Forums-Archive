---
title: "Dell XPS 1530, nvidia drivers problems"
date: 2008-06-12
forum: Hardware
---

### Post by semafor on 2008-06-12
Hi.

Whenever I enable nvidia drivers on Ubuntu 8.04 and restart gdm, gdm starts with an white/grey screen. After a short while, a black vertical border materialize on the screen.

The screen looks similar to when you crush a LCD. With no driver (or default xorg.conf), everything works fine.

I've search the forums only to find one similar thread which had no replies.

Anyone have any idea of what I can do? My xorg.conf is configured by the nvidia tool.

---

### Post by raghuramos1987 on 2008-06-22
samw problem here... worked fine till i upgraded to hardy... :(

---

### Post by veedub on 2008-06-22
There are new drivers in the repositories.  install "nvidia-glx-new-envy", and select version 173.14.05.

---

### Post by raghuramos1987 on 2008-06-22
this thread did the trick... working fine with beta driver after doing the upgrade stuff [http://ubuntuforums.org/showthread.php?t=776802&page=5](http://ubuntuforums.org/showthread.php?t=776802&page=5) :)

---

