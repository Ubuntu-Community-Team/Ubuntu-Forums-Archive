---
title: "CD unmounts automatically after a few minutes"
date: 2010-10-27
forum: Hardware
---

### Post by JimmyJoeBob on 2010-10-27
Hi everyone,

Recently, I have been having some problems with my CD.  I put a disk in when I am starting up my system, and Ubuntu automagically mounts it like normal.  However, after about 10 minutes, the disk magically unmounts itself and will not eject or remount.

This isn't a huge probelm for me since I rarely use CDs, but it would be good to fix.  For reference, I have Ubuntu 10.04 x86_64.  I tried looking around for information on this but couldn't find anything.

Thanks!

---

### Post by JimmyJoeBob on 2011-06-13
I hate to drag up old threads, but this is still going on.  I did a bit of research; everything I found pointed to a kernel bug or a driver issue.  None of the bugs reported matched my symptoms exactly though, so if anyone has any idea of what might be going on I would be happy to hear about it.

---

### Post by tgalati4 on 2011-06-14
Open a terminal:

dmesg | tail -f

When it pops open, take note of the messages.  My thinkpad t43p cd pops open randomly.  I haven't researched it.

---

