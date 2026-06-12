---
title: "Slow screen drawing with nVidia card *sometimes*"
date: 2007-07-02
forum: Hardware &amp; Laptops
---

### Post by xen on 2007-07-02
Sometimes when I boot my computer, everything is fine.

Most of the time however, the screen performance isn't very good. By this I mean that resizing windows is unresponsive, and so is minimizing maximizing windows. The performance just doesn't feel acceptable, it was much better on my previous graphics card (7600GT). Although saying this, 3D performance is apparently unaffected, it works fine whether the computer has booted into 'working' mode or not.

My current graphics card is an nVidia 8600GTS. I'm using the latest graphics drivers from nVidia and I'm running Feisty 64bit. Like I said, sometimes everything works fine, but it seems to be chance. I have checked 'dmesg' for any diagnostics but I haven't noticed anything that would appear to be the cause of the problem.

I have tried various different window managers, and I'm currently using XFWM since I prefer this. Please note that I am *NOT* using Beryl/Compiz.

I will attach my xorg.conf and xorg.0.log. (The log is split into 2 files due to txt file size limit on the forum).

My experiences are very similar to those of these threads:
[http://ubuntuforums.org/showthread.php?t=312356&highlight=nvidia+window+resize](http://ubuntuforums.org/showthread.php?t=312356&highlight=nvidia+window+resize)
[http://ubuntuforums.org/showthread.php?t=484680&highlight=nvidia+window+resize](http://ubuntuforums.org/showthread.php?t=484680&highlight=nvidia+window+resize)

EDIT: Forgot to mention that gnome-system-monitor shows 100% CPU when moving or resizing the windows. It doesn't seem to be the fault of any one process however.

---

