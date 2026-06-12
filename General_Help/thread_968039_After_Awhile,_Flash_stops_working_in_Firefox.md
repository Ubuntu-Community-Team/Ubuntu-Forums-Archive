---
title: "After Awhile, Flash stops working in Firefox"
date: 2008-11-02
forum: General Help
---

### Post by pimpsahoy on 2008-11-02
I've noticed in Ubuntu 8.04 that flash stops working after X minutes of browsing.  A restart (of firefox) usually does the trick.  Now, in 8.10, the same thing happens and I still get that problem, however, a refresh of Firefox usually does the trick.  Normally, wherever flash should be (a youtube video, game, etc) a grey box appears.  How can I fix this (I've tried reinstalling the flash plugin).

---

### Post by gerber on 2008-11-14
Just trying to push this topic up a little ;-)
... by reporting that the very same happens to me every now and then with Firefox 3.0.3 on 64-bit Ubuntu 8.10 (Gnome). 
I have the latest flash player installed (10.0.12.36).

(Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.0.3) Gecko/2008101315 Ubuntu/8.10 (intrepid) Firefox/3.0.3)

---

### Post by Yashiro on 2008-11-14
There is no fix yet. If you check your running processes you will see a few instances of 'npviewer.bin' running and eating alot of cpu cycles.

It seems this process hosts the flash content, and well, it just crashes or fails to close correctly.

To unlock a crashed browser, just killall npviewer.bin processes.

---

