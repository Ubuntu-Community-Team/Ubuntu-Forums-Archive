---
title: "[SOLVED] Mount RAM as disk"
date: 2008-08-20
forum: General Help
---

### Post by AndyCee on 2008-08-20
Ok - I don't expect this to be a long thread.

In one of my Uni classes, it was shown how in OSX it is possible to mount a section of RAM as disk space in the filesystem.

Can someone show me a command that would do that for Ubuntu? I can imagine the concept being useful for, say, high security. Or perhaps for very fast disk access.

If it is possible in Ubuntu? And can anyone who's done it post what they use it for?

---

### Post by elasto1mania on 2008-08-20
HI AndyCee,

Here is the link [http://https://answers.launchpad.net/ubuntu/+question/8127]("http://https://answers.launchpad.net/ubuntu/+question/8127")

But when you power off the ram the data will be erased.
You could try to make an external power for the ram.

Hope it helps.

---

### Post by bingoUV on 2008-08-20
It is already there on your system: see /dev/shm.

It may be too small, or too big for your requirement. Quick googling gives me this: [http://www.vanemery.com/Linux/Ramdisk/ramdisk.html](http://www.vanemery.com/Linux/Ramdisk/ramdisk.html)

---

### Post by AndyCee on 2008-08-20
Ah, I think I found it:
[http://en.wikipedia.org/wiki/Tmpfs](http://en.wikipedia.org/wiki/Tmpfs)

Thanks for the effort :).

---

