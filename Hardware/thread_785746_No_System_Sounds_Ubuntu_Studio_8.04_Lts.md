---
title: "No System Sounds Ubuntu Studio 8.04 Lts"
date: 2008-05-07
forum: Hardware
---

### Post by petrafan007 on 2008-05-07
I have a problem that I think, based on my research, a lot of people have the same issue but no one seems to be able to figure it out. The only resolution I've seen is trying to jump through hoops and get pulseaudio working, but both times I tried that, sound got screwed up even more and stopped working altogether and I had to figure out how to get the alsa drivers reset so I could at least get sound back on my music/video/etc. I installed esound over pulseaudio and all my sounds worked but then my computer would go slower and slower and almost freeze (and terminal won't show a command prompt when I opened it).

So, my question to ya'll is...is there another way to get sound working without using a sound server a la pulseaudio? Why can't it work with my ALSA?

Sound card: M-AUDIO DELTA 1010LT (works great in Jack/Ardour btw...WHEN things work right...)

---

### Post by petrafan007 on 2008-05-07
So has anyone else had this problem and/or fixed it?

---

### Post by DocBob on 2008-05-08
I read somewhere that the Alsa drivers aren't available or functioning properly in hardy heron just yet. I'd try the oss if possible, which isn't possible for me and, also, I had a problem on Gutsy Gibbon with Ubuntu Studio. My sound was working fine until I installed the Ubuntu Studio then, it wouldn't work and i couldn't figure it out so, I just reinstalled Gutsy gibbon. Good Luck, Also, u might want to check up on the Alsa site: [http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page) regarding any updates.

Also, check my last post. Perhaps might help, worth a shot: [http://ubuntuforums.org/showthread.php?t=786234](http://ubuntuforums.org/showthread.php?t=786234)

---

