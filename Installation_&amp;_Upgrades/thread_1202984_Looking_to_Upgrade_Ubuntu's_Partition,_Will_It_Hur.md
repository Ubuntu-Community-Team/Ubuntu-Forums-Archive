---
title: "Looking to Upgrade Ubuntu's Partition, Will It Hurt Vista?"
date: 2009-07-02
forum: Installation &amp; Upgrades
---

### Post by jeremyj on 2009-07-02
Hi, all, I'm looking at upgrading Ubuntu to the 9.04 release from 8.10 via the Updates Manager.  I'd like to know if anyone has experienced any problems with Ubuntu erasing the Windows partition during the upgrade process?  Specifically, in this case it's Vista.

You'd think this would be a simple question to answer, but here's the catch, and the reason I'm concerned with upgrading:

[http://ubuntuforums.org/showthread.php?t=1051887&page=2]("http://ubuntuforums.org/showthread.php?t=1051887&page=2")

Posts 12, 14, and 18 are the key info related to this question/thread in the above link.

I posted this when trying to install Ubuntu on this desktop, and the Partitioner gave me a different view of how it would be installed than the simple, "Ok, let's create/use an existing separate partition, and leave alone Vista and the entire empty space you have."  Here is the screenshot I added in post 14 of that thread of the Partitioner/GParted confusion:

[http://ubuntuforums.org/attachment.php?attachmentid=101389&d=1233228240]("http://ubuntuforums.org/attachment.php?attachmentid=101389&d=1233228240")

Has anyone experienced Ubuntu erasing all other partitions, such as Vista, when upgrading via the Updates Manager?  Would anyone think that this is possible given what I experienced with installation/Partitioner in the links above?

Many thanks in advance!

---

### Post by Hobgoblin on 2009-07-02
If you do an upgrade from the update manager then it won't change any of your partitioning.  You won't go through the partitioning options again so won't encounter any of those issues.

> **jeremyj said:**
> 
I posted this when trying to install Ubuntu on this desktop, and the Partitioner gave me a different view of how it would be installed than the simple, "Ok, let's create/use an existing separate partition, and leave alone Vista and the entire empty space you have."  Here is the screenshot I added in post 14 of that thread of the Partitioner/GParted confusion:

[http://ubuntuforums.org/attachment.php?attachmentid=101389&d=1233228240]("http://ubuntuforums.org/attachment.php?attachmentid=101389&d=1233228240")

Has anyone experienced Ubuntu erasing all other partitions, such as Vista, when upgrading via the Updates Manager?  Would anyone think that this is possible given what I experienced with installation/Partitioner in the links above?


What you should have done there is the first option (Guided - resize SCSI1).  Which is usually the default selection (or, as you did, manual partitioning).

---

### Post by Sef on 2009-07-02
Before upgrading:

1) **Back up** your **data**.   There are not 100% guarantees that all will go well.

2) Have a live or alternate cd or both available in case you need to reinstall the os that you upgraded from.

---

### Post by jeremyj on 2009-07-03
I'm backing up my files as I type this, just in case.  Thanks for the replies, Hobgoblin and Sef.

> **Hobgoblin said:**
> What you should have done there is the first option (Guided - resize SCSI1).  Which is usually the default selection (or, as you did, manual partitioning).

It's been a while since I did that, but I think I remember that GParted didn't recognize my newly created partition to which I was trying to install it.  I could have always resized it, I guess, if I let it use the entire empty space on my HDD, but I felt like that would be a step back or something.  Turns out it was more work to get it into that separate partition.  Who knows?  :lolflag:

> **Sef said:**
> Before upgrading:

1) **Back up** your **data**.   There are not 100% guarantees that all will go well.

2) Have a live or alternate cd or both available in case you need to reinstall the os that you upgraded from.

I'll be burning a Live CD of 9.04 as well since I still have my original 8.10 disc.  Thanks again for the advice!

---

### Post by jeremyj on 2009-07-07
Sorry for the delay in this reply.  It's been a busy holiday weekend.  I just wanted to touch base again, and say that all went well with the upgrade.  Synaptic worked like a charm, and didn't touch Vista even after the problems I had with GParted on the Live CD back when I installed 8.10.  I do have a different question now regarding extending my Linux partition 10 gigs, but I figure that's another question for another thread.

Thanks again for all the advice!

---

