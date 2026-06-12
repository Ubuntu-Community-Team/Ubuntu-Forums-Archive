---
title: "xf86-video-intel"
date: 2008-11-29
forum: General Help
---

### Post by cqr on 2008-11-29
Hi everyone!
Interpid comes with the 2.4.1 version of the intel drivers (i have a x3100), and the 2D performance is noticeably worse then that of the 2.2.1 (so the  one in hardy). I tried 2.3.x aswell and the only one i can for example scroll flawlessly is 2.2.1 . Is this possible? Do i have somethin screwd up? I even tried 2.4.99 and that was even worse then 2.4.1 ... So is there anyone experiencing somethin like this, or any fix for it?
Thx in advance!

---

### Post by fedex1993 on 2008-11-29
It might actually not be your video drivers might be your ram.

---

### Post by cqr on 2008-11-29
So later drivers needs more ram..? (have 1 GB actually, with celeronM 550)
I cant imagine how is that possible to not even be able to scroll normally with the newer drivers.. 
I tried downgrading xorg with aptitude but it screwed up the system..
Any idea? Is it only me? No one else experiencing this (2d and 3d performance problems with newer driver)?

---

### Post by Locutus_of_Borg on 2008-11-29
you'll probably have to downgrade xorg and mesa and maybe a few other things (libdrm maybe?) in order to use the older intel driver....not exactly sure how to in ubuntu, but compiling it yourself shouldnt be too hard

---

