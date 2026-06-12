---
title: "EPIA ME6000 minimal install problem with starting X (icewm / wdm)."
date: 2009-02-11
forum: Installation &amp; Upgrades
---

### Post by davemar on 2009-02-11
I've been vaguely following the instructions here [http://www.psychocats.net/ubuntu/minimal]("http://www.psychocats.net/ubuntu/minimal") to install a minimal system on my EPIA ME6000 board. I've gone for the variation at the bottom with the icewm and wpm setup.

All the things installed OK, but when I do ```
sudo /etc/init.d/wdm start
``` it gets as far as the fine checkerboard screen with the mouse-cross in the middle, then the screen goes blank and that's that.

Is there something awkward with the EPIA board when it comes to X, that I need to tweak to get it running?

---

### Post by davemar on 2009-02-13
I turned the machine on again yesterday, and lo and behold, the window manager worked! Don't know why it decided to start working, but it does now; maybe it just needed a full restart to get things reset properly. Next job: getting ALSA working....

---

