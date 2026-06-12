---
title: "[SOLVED] Need more HD SPACE"
date: 2008-08-22
forum: General Help
---

### Post by hsienloong on 2008-08-22
Hi I got a 70gb HD, when I installed Ubuntu I somehow messed up.
So now my Ubuntu partition has 12 gb of HD space and my XP partition has the rest of the 70 gb. 

I installed so many helpful Ubuntu apps and saved so many importnant files on my Ubuntu partition ------I DONT WANT TO REINSTALL

so is there a way or a applicaton which manages partitions

so I can get more space on my Ubuntu Partition??

-hsienloong

---

### Post by sandysandy on 2008-08-22
use gparted Cd to resize both windows (shrink) and Ubuntu (expand)

gparted URL

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/) (burn as iso image)

gparted tutorial

[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

regards

---

### Post by CowboyFunk on 2008-08-22
Boot up the live cd and use gparted

---

### Post by tamoneya on 2008-08-22
> **sandysandy said:**
> use gparted Cd to resize both windows (shrink) and Ubuntu (expand)

That is the way I would do it but there are a couple of things you should think about first.

1. For windows make sure you defragment first.  It will move the data around on the disk and it will decrease the chances of errors.
2. Also since messing with partitions is a potentially dangerous operation you should backup any critical files in case there are some problems.

---

