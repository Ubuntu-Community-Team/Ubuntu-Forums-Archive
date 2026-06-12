---
title: "Black screen, unresponsive after lid close?"
date: 2006-11-02
forum: Hardware &amp; Laptops
---

### Post by rancourt on 2006-11-02
Beg your pardon, friends. I'm finding myself in a bit of a spot with both Dapper and Edgy. (Currently running Edgy on a Dell XPS M140 with Intel 915GM video array running the i810 driver, DRI up and running successfully.)

When I close the lid of my laptop while it's running and later reopen it, the screen is black and unresponsive, although hard disk and wireless activity lights flicker. Attempts to switch consoles seems to yield no result, and attempts to type through the "darkness" to sync;sync;sync and sudo reboot now yield nothing. Web searches and forum searches have yielded some suggestions (changes to another version of lid.sh), but I haven't managed to adapt their suggestions into a solution.

This is proving problematic for me. Might anyone be able to help me work through this?

Many thanks in advance.

---

### Post by RafRaf on 2006-11-03
Hi,

Following these instructions seams to help a lot of people:
[http://ubuntuforums.org/showthread.php?t=287052](http://ubuntuforums.org/showthread.php?t=287052)

If not, you could try to install the package "hibernate"

---

### Post by rancourt on 2006-11-06
I appreciate the tip -- thank you. It doesn't seem to have helped, in my case. I'm going to try running X with the -noacpi option, and see how it behaves.

---

### Post by dolphinsonar on 2006-11-21
Hit Ctrl Alt F1 then Ctrl Alt F7.

Its ghetto but it will get your screen back on.

---

