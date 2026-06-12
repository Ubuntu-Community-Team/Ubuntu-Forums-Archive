---
title: "Missing Firefox Icons"
date: 2008-08-20
forum: General Help
---

### Post by grjemo on 2008-08-20
I just used this HOWTO: [http://ubuntuforums.org/showthread.php?t=202537](http://ubuntuforums.org/showthread.php?t=202537)

It worked fine, but my 32-bit copy of Firefox has almost no icons.  Most are replaced with a little page with a red "x" in the middle.  64-bit firefox still works fine, however.  Any ideas?

---

### Post by phillik747 on 2008-09-29
I had the same problem. It's down lower in the tutorial on how to fix this. 

> Missing Icons for some themes
As pointed out by darthcloud. Open a terminal, enter the following.
Code:

gksudo gedit/usr/local/bin/firefox32-3

Change this line

linux32 /usr/local/firefox32-3/firefox $@
to
/usr/local/firefox32-3/firefox $@

Save the file and restart your browser.

:)
Kyle

---

