---
title: "Migrate OS to different HDD?"
date: 2008-06-07
forum: Hardware
---

### Post by ArchCorsair on 2008-06-07
Hey, I'm just wondering if it's possible to transfer my installation of Ubuntu 8.04 to another, bigger harddrive without having to reinstall it.

thanks

---

### Post by logos34 on 2008-06-07
Affirmative.

Use Partimage, Gparted or dd:
[http://gparted.sourceforge.net/larry/move/move.htm](http://gparted.sourceforge.net/larry/move/move.htm) 
(too bad the example is NTFS, but the principle is the same for ext3)
[http://ohioloco.ubuntuforums.org/showthread.php?t=287522](http://ohioloco.ubuntuforums.org/showthread.php?t=287522)
[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)

If you plan on keeping the old drive in the machine, you might also consider simply moving /home to a separate partition on the bigger drive.  It's by far your largest directory, and a bit easier to do than moving root. (although it can look daunting to noobs).

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

