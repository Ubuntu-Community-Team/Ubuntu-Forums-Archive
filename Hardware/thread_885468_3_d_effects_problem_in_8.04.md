---
title: "3 d effects problem in 8.04"
date: 2008-08-10
forum: Hardware
---

### Post by masterbrumm on 2008-08-10
Hi i have been struggeling with my ati x1650 agp card for about 14 days to get the 3d effects to work, after many many unsuccesful tries i finally made it after changing my agp size in bios and installed envy. But now have a new problem, while running compiz /3d effects , my vidoes is flickring. My 3d apps. and games does the same so i have to disable 3d effects to use them. There is big problems with graphics in wine. 

Any ideas?
Thanks

---

### Post by stinkinrich88 on 2008-08-10
yeah, I've regretting switching to ATI ever since I did. Mipmaps and blur don't work in compiz, using ati open drivers with 4gb of ram is a challenge and all openGL apps (google earth, etc) flicker with compiz enabled. 

What video are you on about? If you're using VLC player and it's flickering then do this:

open vlc -> settings -> preferences -> video -> output modules -> check "advanced options" -> select "X11 video output" from the drop down list.

srsly, though, your ati card is going to be a challenge. Nvidia? no problems at all.

---

### Post by masterbrumm on 2008-08-10
Okey thanks a lot for helping  i will try vlc player hopefully it works, yeah maybe i should consider an nvidia card instead, I really need to use wine.
I tried to change config in wine, but i cant get it to work right looks like a mess.

---

