---
title: "How to fix boot error, please help?"
date: 2009-02-03
forum: Installation &amp; Upgrades
---

### Post by philidox on 2009-02-03
Every time I boot my computer to ubuntu, it has some kind of error that auomatically logs in as root and request me to press control D to continue the boot sequence.  It goes on to tell me that the error is saved in the /var/log/fsck folder.  I check it myself there is the log

_____________________________________________________________________________
Log of fsck -C -R -A -a 
Tue Feb  3 19:02:35 2009

fsck 1.40.8 (13-Mar-2008)
VIDEO: clean, 1425/61054976 files, 69164045/244190000 blocks
fsck.ext3: Unable to resolve 'UUID=6caa21bc-b40f-42d3-956a-62d081288721'

fsck died with exit status 8

Tue Feb  3 19:02:36 2009
----------------
___________________________________________________________________________

After I press Ctrl+D, it boots up normally with no issues, however it is kinda annoying that I have to go thru this process everytime I restart my computer. Anyone one got any idea on how to remedy this issue?

---

### Post by hansdown on 2009-02-03
Hi philidox.

This solved thread should help.

[http://ubuntuforums.org/archive/index.php/t-957929.html](http://ubuntuforums.org/archive/index.php/t-957929.html)

---

