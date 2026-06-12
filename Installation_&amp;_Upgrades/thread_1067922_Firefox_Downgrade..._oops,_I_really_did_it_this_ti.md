---
title: "Firefox Downgrade... oops, I really did it this time..."
date: 2009-02-12
forum: Installation &amp; Upgrades
---

### Post by benf101 on 2009-02-12
Well, after a stroke of genius, I officially took-out any ability to ever run Firefox again.

Aptana studio just had to use Firefox-2.  I had Firefox-3.  Some website said that if you have Firefox 3 that you need to type in sudo apt-get install firefox2... But it made me uninstall Firefox 3 first.

After uninstalling FF3, I "successfully" installed FF2 but it wouldn't run.  So I tried to go back and reinstall FF3 and that says it's successful but it won't run either.  So I tried uninstalling everything Firefox and reinstalling FF3.  No dice.

The error message that comes up says "Firefox is already running, but is not responding. To open a new window, you must first close the existing Firefox process, or restart your system."

Restarting doesn't work, FYI.

Any ideas?

---

### Post by dstew on 2009-02-12
Maybe first try to repair whatever firefox is left by```
sudo apt-get update
sudo apt-get upgrade
```
If you want to get rid of all traces of a program that was installed using apt-get, you sometimes need to use```
sudo apt-get remove **--purge** firefox2
``` or firefox3 if you want to remove that.

---

### Post by benf101 on 2009-02-12
That did not seem to help.  Anything else I should do next?

By the way, just for the benefit of anyone else using this post, use the command **sudo apt-get remove --purge firefox-2**, not sudo apt-get remove --purge firefox2.  (Notice the hyphen after firefox).

---

### Post by benf101 on 2009-02-12
Solved:
[http://ubuntuforums.org/showthread.php?t=453204](http://ubuntuforums.org/showthread.php?t=453204)

During my upgrade to aptana, I had to add a new profile.  Typing "firefox -ProfileManager", then deleting the aptana profile solved it.  I hate when that happens.

---

