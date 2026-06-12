---
title: "no options at 'prepare partitions' step"
date: 2009-01-06
forum: Installation &amp; Upgrades
---

### Post by brydong on 2009-01-06
My thinkpad x61 has problems and I can't login my ubuntu instance. I'm able to get in by booting off a usb drive instance of 8.10. I'm trying to install 8.10 to see if that 'fixes' the issue. When I reach step 4, prepare partitions, I don't appear to have any options to move forward, see attached. I am able to browse to the resident hard drive using nautilus.

help?

thanks,
brydon

---

### Post by brydong on 2009-01-07
I figured it out. In peeking at the data, clearly that drive was mounted. Unmounting the drive made it visible to installer and partitioner.

---

### Post by tac-tics on 2010-04-11
I'm having the same issue. I tried once from the Live CD Gnome environment, and there were no options at the Prepare Partitions screen. I don't believe my disk was mounted. Regardless, when that didn't work, I rebooted my computer, and selected Install Linux instead. When I got to the Prepare Partitions screen again, I had the same problem.

---

### Post by tac-tics on 2010-04-11
Solved my problem using

[http://ubuntuforums.org/showthread.php?t=1380077](http://ubuntuforums.org/showthread.php?t=1380077)

My case was a slightly different situation. I purchased a new mobo which had raid support. Even though I wasn't using the raid, the installer didn't know that. The solution is to apt-get uninstall the dmraid package from the live cd desktop environment, then run the install.

---

