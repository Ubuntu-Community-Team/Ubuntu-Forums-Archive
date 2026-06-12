---
title: "Ubuntu 12.04 not recognizing floppy drive"
date: 2013-09-03
forum: Hardware
---

### Post by MichaelaRBrown on 2013-09-03
I just installed 12.04 LTS on my grandfather's computer. Being, well... a grandfather, he still uses floppy disks (which I respect, because it's cool). However, when we plugged in his USB floppy drive, Ubuntu didn't read it. We tried multiple disks to no avail.

I read somewhere that this is a problem with GParted, but I wasn't sure. If so, is there a way to work around it? It's not a big deal, but it's become a matter of pride. I WILL GET THIS OS TO READ THESE STUPID DISKS!

---

### Post by bkline on 2013-09-03
Not a grandfather (yet), but my Linux system still reads floppies.  It's not as easy as it used to be, though.  You might want to read this long-standing bug report to find out why, and how to work around the fact that Linux no longer recognizes floppies as automatically as it used to:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/441835](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/441835)

Warning: it's kind of long-winded, and gets a little flame-war like in places, but should provide you with the workaround you asked for.

---

### Post by jglen4902 on 2013-09-21
Yep, long-winded and short on helpfulness.  Bottom line, someone dropped floppy drive support, and no one is interested in fixing the problem in current versions (including LTS) of *buntu.  Have to wait until udisks version 2.0, and the "work-around" is to upversion to something that has udisks 2.0, because it won't be backfilled to earlier versions like 12.04.

---

### Post by jglen4902 on 2013-09-21
I was having the the same problem in Kubuntu 12.04 after recently installing a floppy drive to access some old diskettes with some important information on them.  I beat my head on that brick wall for quite a while until I found a thread in the kubuntuforums.net.  [Enable Your Floppy Drive]("http://www.kubuntuforums.net/showthread.php?58581-Enable-your-floppy-drive&p=335635#post335635") You will probably need to "adapt" as it's specific to the KDE environment.

Basically, you end up with a "Mount Floppy" link in the KDE kicker ("start") menu, and you unmount it with another menu entry from an item set up in the Desktop folder in Dolphin.  It works, but it's a kludge.

You could probably also just use "udisks" commands in a console to mount and unmount a diskette.

---

