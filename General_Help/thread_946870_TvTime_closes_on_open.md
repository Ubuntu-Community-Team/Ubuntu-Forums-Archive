---
title: "TvTime closes on open?"
date: 2008-10-13
forum: General Help
---

### Post by scriptox on 2008-10-13
Hey all, im new to ubuntu, like really completely new. Previously while using windows xp i was able to install a driver to use my eyetoy as a webcam. Coming to ubuntu i did the same thing, only a little different. I realized that XawTV would go to a full-black screen when opening. So i heard that Tvtime works way better. I installed that and when trying to open it as well, it would flash a small black window then dissapear. Nothing would happen. Why does it automatically kill itself? Can I fix XawTV or TvTime at all?

---

### Post by fragos on 2008-10-13
IMHO tvtime is much better. Open a terminal window and run "tvtime" there. In all likelyhood it will provide error messages on the terminal that will direct you to a solution. The problem may be your type of TV card. on the terminal run "lsmod |grep tv". If you see lots of references to bttv it should work. If on the other hand it ittv tvtime won't work for you. Your choice of TV application will be limited to mythtv and and perhaps xawtv. [http://tvtime.sourceforge.net/](http://tvtime.sourceforge.net/) has the details of what will and won't work.

---

