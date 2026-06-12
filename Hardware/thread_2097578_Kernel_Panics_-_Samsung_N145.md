---
title: "Kernel Panics - Samsung N145"
date: 2012-12-23
forum: Hardware
---

### Post by Joshun on 2012-12-23
Ubuntu seems to be having occasional kernel panics on bootup on my Samsung NP-N145 netbook. No idea why. Anybody else having this problem? (I use Xubuntu that wouldn't make any difference).

See images attached - I can't seem to get any logs of the boot - only the boots before and after.

Joshun

---

### Post by Joshun on 2012-12-27
Forcing fsck to check both / and /home (I have /home on a separate partition) seems to have stopped it for now - I ran ```
sudo touch /forcefsck
``` and ```
sudo touch /home/forcefsck
```. I also reduced the number of mounts before the filesystems are next checked using ```
sudo tune2fs -c 20 device
``` (setting it to 20 mounts). Hope this is useful for anyone having kernel panics. I'll leave it for a bit to make sure this is definitely solved, and if it is I'll then mark the thread as solved.

---

