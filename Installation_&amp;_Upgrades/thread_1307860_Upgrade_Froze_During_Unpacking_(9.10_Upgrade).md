---
title: "Upgrade Froze During Unpacking (9.10 Upgrade)"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by chad724 on 2009-10-31
I started the upgrade to 9.10 2 days ago. It took hours to download, but it finally finished downloading, and it started installing. Then about half way through, the computer froze. It just completely froze when it was unpacking. I left it on all night, but yesterday morning it was still frozen. So I had to coldboot it.
 
Then I restarted my computer, and tried to boot into "Ubuntu 9.04" but upon booting, it gave an error (not to my surprise) that something could not be mounted that is in etc/fstab (I can find that error if I need to again, by trying to boot into it again).
 
But my question is, can I finish unpacking the files if I boot into a livecd? Where are the files stored for unpacking, if I can do that, and what would I need to do? Or can I even start the upgrade again somehow, say, with a livecd of 9.10?
 
Thanks!

---

### Post by chad724 on 2009-11-01
I fixed it after getting "professional" help. Anyway, while in the recovery shell, I used these commands:

mount -n -o remound,rw /
dpkg --configure -a


I really wish people like me could get a bit more support. And I'm still looking for help with this issue, now that I'm on 9.10: [http://ubuntuforums.org/showthread.php?t=1291286](http://ubuntuforums.org/showthread.php?t=1291286)
I'm experiencing the exact same thing.

---

