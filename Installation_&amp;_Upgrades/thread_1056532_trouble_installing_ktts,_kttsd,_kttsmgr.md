---
title: "trouble installing ktts, kttsd, kttsmgr"
date: 2009-01-31
forum: Installation &amp; Upgrades
---

### Post by kline on 2009-01-31
Guys,

I had similar problems about 4 years ago but got them resolved.  Now, with 8.10, I'm wedged again.

The parrot icon is there, and the kttsmgr binary is there but I can't get the basics to install. Specifically, the first line in General, the General tab,  

[B][CENTER]"[] Enable Text-to-Speech System (KTTSD)"
[/CENTER][/B]
is greyed out.  An hour ago I installed the festival suite and a couple other, independent tts programs.  I set up things in the Notification and Audio tabs.  I tried to choose a speaker from the festival group.  These fail to install.  Any ideas?

gk

PS:  If this should be posted to another forum, please let me know which!
PPS: aRts is running and selected in the kttsmgr widget... .

---

### Post by kline on 2009-02-01
The problem was that there were no talkers installed; in other words, festival had not installed any voices --diphones??--.  That was why the "test" failed and the rest of the kttsmgr installation didn't work.  It seems to me that if kttsmgr knows that there are no voice files, the program should pop-up an appropriate warning dialog.

(*****)

---

