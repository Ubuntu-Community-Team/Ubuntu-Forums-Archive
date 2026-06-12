---
title: "Disk space filled up, no idea why"
date: 2008-08-16
forum: General Help
---

### Post by markdjones82 on 2008-08-16
All,
  My root disk space filled up and I cannot figure out why.  All of a sudden it just filled up like a log was expanding or something.  I can't think of anything i instaleld that would have caused this.

I run du and it doesn't really give me anything.  Logs don't seem to be filled.  I ran a few commands to find large files and nothing came up.  I rebooted no luck.  Anyone have any suggestions, I'm dyin over here!

---

### Post by Vivaldi Gloria on 2008-08-16
Delete root's trash.

---

### Post by markdjones82 on 2008-08-16
Ok, I figured out what it was and man this was a doozy.  I had to get sherlock holmes on this one.

Ok, so I booted into my ubuntu, but my external drive did not mount to /media.  Well, I had a backup kick off and it filled /media up with the backup in the background that I didn't notice.  While I was browsing around that hey my external drive isn't mounted.  So, I mounted it on top of /media after the backup put the data on the local /media. I finally ended up unmounting everything and figuring out that it filled /media on the local fs and not my mount.

So, lesson learned from all, if you get a full FS make sure you didn't move stuff to a mount point before you mounted on accident.

:lolflag:

---

