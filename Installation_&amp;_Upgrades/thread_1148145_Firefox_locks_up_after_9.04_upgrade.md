---
title: "Firefox locks up after 9.04 upgrade"
date: 2009-05-04
forum: Installation &amp; Upgrades
---

### Post by Lido on 2009-05-04
I was running 8.10 Amd64 fine for the past year and just upgraded the system through the update tool to 9.04. Most things seem to be ok, the usual little issues (e.g. no spdif sound in Mythtv), but one big big issue is that Firefox is locking up my system every time I try to run it. I've tried ctrl-alt-del and alt F8, but I can't drop out of x to a normal command line session and I can't switch consoles so I just have to hit the reset button on the case. Anyone else having this issue?

---

### Post by Lido on 2009-05-04
Reinstalling didn't help by the way.

---

### Post by Lido on 2009-05-05
Any ideas?

---

### Post by dstew on 2009-05-05
A corrupted profile will cause firefox to die in many different ways. See [this thread]("http://ubuntuforums.org/showthread.php?t=826510") and  [this article]("http://support.mozilla.com/en-US/kb/Basic+troubleshooting"), especially the part about your profile. I recently went through a repair of a Firefox profile on my wife's Windows machine. It is not clear why the profile may get corrupted, but it is a problem with Firefox that can lead to the problem you are having.

---

### Post by Lido on 2009-05-08
Thanks, that did the trick. I just typed this in the terminal:
```
firefox -profilemanager
```
and then deleted the profile and then quit and started up Firefox normally and all was well. I didn't have any bookmarks so I wasn't worried about losing anything.

---

