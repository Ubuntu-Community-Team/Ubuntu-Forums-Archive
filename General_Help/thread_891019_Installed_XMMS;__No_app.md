---
title: "Installed XMMS;  No app"
date: 2008-08-15
forum: General Help
---

### Post by Sam324 on 2008-08-15
Hi.  I installed XMMS media player recently (main file(s) and a bunch of plugins), but there are no links under any of the headers in the Applications menu, and typing "xmms" in the terminal yielded no results.  What do I do?

---

### Post by Raffles10 on 2008-08-15
I had the same problem with XMMS, I don't think it's supported in Hardy Heron, it's not available in repositories.

Give [Audacious]("http://audacious-media-player.org/index.php?title=Main_Page") a go, it's like a XMMS clone.

---

### Post by cariboo on 2008-08-15
You more than likely installed xmms2 if you search in synaptic for **xmms2 client** you should be able to find a front end for xmms2.

Jim

---

### Post by cozmicharlie on 2008-08-16
Try this tutorial for installing XMMS.
[http://ubuntuforums.org/showthread.php?t=833164&highlight=shn](http://ubuntuforums.org/showthread.php?t=833164&highlight=shn)

---

### Post by eggdeng on 2008-08-16
Run
```
sudo updatedb
```
then
```
locate xmms
```
If it is installed, this will tell you where.
You can then run it using /path_to_file/xmms (or xmms2).

---

