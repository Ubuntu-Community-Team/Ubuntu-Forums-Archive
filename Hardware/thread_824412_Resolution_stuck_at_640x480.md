---
title: "Resolution stuck at 640x480"
date: 2008-06-10
forum: Hardware
---

### Post by amirage on 2008-06-10
Hi all

I just installed new updates in Ubuntu Hardy Heron and apparently a new kernel was also installed. When I boot into the new kernal neither the video card nor the sound card is recognise. When I boot into the old kernal, everything is alright except for the resolution. It's stuck at 640x480. There's hardware accelaration, but the resolution is stuck. The card I have is nvidia 6800LE.

Is there a solution to rectify this. I'm just a novice to linux and am loving it. I don't know any coding but will be willing to learn.

If all else fails, does any one know how to undo the updates that were installed?

Please let me know...

Amit

---

### Post by bahmak2003 on 2008-06-10
I have that problem with my laptop. What I did is boot gutsy 7.10 live cd then copy or save the /etc/X11/xorg.conf and then boot hardy 8.04. Edit hardy's xorg.conf with that copy of gutsy 7.10.

---

