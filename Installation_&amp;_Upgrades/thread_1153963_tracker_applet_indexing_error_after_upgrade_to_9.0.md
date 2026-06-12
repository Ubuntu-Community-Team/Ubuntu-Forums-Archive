---
title: "tracker applet indexing error after upgrade to 9.04"
date: 2009-05-09
forum: Installation &amp; Upgrades
---

### Post by findlj on 2009-05-09
After upgrading to 9.04 from 8.10, I get an index corruption error window repeatedly from the tracker applet.  Anyone else experienced this and if so, how did you fix it?
Thanks for the help.

---

### Post by davisch on 2009-05-11
I am having the same problem.  I can stop the two tracker processes but they invariably get restarted and soon my cpu is running at 100%.  Most annoying.  I guess I need to check to see if tracker is a chron job or only gets started at reboot?  Sorry I can't help you.  They only solution I found when searching was to turn off tracker but that doesn't fix it - just avoids the problem...

---

### Post by funkygiblet on 2009-05-11
I am also experiencing the same, but only if I plug in a USB key.

---

### Post by davisch on 2009-05-11
It appears that this is a documented bug and there is a work around see tha posting in the bug list

[https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/361560/comments/30](https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/361560/comments/30)

---

