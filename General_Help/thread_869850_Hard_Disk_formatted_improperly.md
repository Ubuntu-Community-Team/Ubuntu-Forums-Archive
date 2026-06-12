---
title: "Hard Disk formatted improperly"
date: 2008-07-25
forum: General Help
---

### Post by Doccie on 2008-07-25
Methinks I made a booboo... 

I installed Linux Mint onto my desktop the other day. I formatted my HD using the LiveCD Install. Later I tried to format my second HD using the GParted release that came with Mint. That didn't go to well (ref: [Gparted forums](http://gparted-forum.surf4.info/viewtopic.php?id=1571)) and I ended up formatting my HD from the terminal, using the info on [this page](http://www.cyberciti.biz/faq/linux-disk-format/).

Unfortunately, that didn't go completely as hoped either. Gparted still doesn't recognize the filesystem (screenshot3.png) and the disk -is- available but it's under /disk2 in my Filesystem drive rather than as a new drive (screenshot4.png).

And on top of that, now if I try to format it again, I get this warning:
/dev/hdb1 is apparently in use by the system; will not make a filesystem here!

Which makes sense I suppose, but doesn't really help :)

So my question, how do I get the second disk to display nicely next to my filesystem drive and my external HD?

---

### Post by fsmithred on 2008-07-25
I use cfdisk to partition drives, so I don't know if fdisk would allow you to get away without specifying the type of partition you want, which is probably 82 (native linux). If that doesn't sound familiar, maybe you should unmount /disk2 and try again.

Another thing you might do is to use the -c option with mkfs to check for bad blocks. It might not help, but it's good practice.

---

### Post by Doccie on 2008-07-25
Thanks, I will definately look into that and post back with the results

---

### Post by Doccie on 2008-07-26
Got it working :) Thanks a bunch. Unmounting /disk2 put me on the right track.

---

