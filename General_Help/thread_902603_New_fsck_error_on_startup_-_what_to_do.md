---
title: "New fsck error on startup - what to do?"
date: 2008-08-27
forum: General Help
---

### Post by jcr1 on 2008-08-27
Last few times I have booted up my server it has started running fsck everytime, at the Usplash bit. It fails and as you know drops you into a root command line asking you to run fsck manually.

Here is my checkfs log:

```

Log of fsck -C3 -R -A -a
Wed Aug 27 18:14:12 2008

fsck 1.40.8 (13-Mar-2008)
/dev/sda2: clean, 3059/2449408 files, 769380/9765511 blocks
/dev/sdb1 contains a file system with errors, check forced.
/dev/sdb1: Inode 14884888 (...) has invalid mode (00).


/dev/sdb1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
        (i.e., without -a or -p options)
fsck died with exit status 4

Wed Aug 27 18:18:43 2008
----------------

```

Now I can tell you that sdb1 is a second HDD.

If I just hit ctrl-D to continue it boots up fine and the sdb1 mounts and works fine.

What to do about the error?

Thanks in advance.

---

### Post by jigsaws on 2008-08-27
Maybe
> RUN fsck MANUALLY.
        (i.e., without -a or -p options) ? :-)

---

### Post by jcr1 on 2008-08-28
heh you're right... gave me a few questions about fixing things, which I did and seems fine now.

Thanks,

---

### Post by littletinman on 2008-09-16
I'm running into a similar error. How did you fix that?

---

