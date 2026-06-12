---
title: "External HD"
date: 2007-11-19
forum: Hardware &amp; Laptops
---

### Post by wydra on 2007-11-19
Hi,

I'm trying to copy some files form Ubuntu to my external Seagate Free Agent 250 Gig HD. For some reason it seems to be set to a read only drive, what's going on?

I can't, "un-readonly" it.

---

### Post by stephantom on 2007-11-19
Which release of Ubuntu are you using?
If your external HD is formatted with the NTFS file system (which it most certainly is), you'll only be able to write to it using the ntfs-3g package. It comes preinstalled in Gutsy, but it's also available in the Feisty repositories.
Just fire up your package manager and follow these instructions:
[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

---

### Post by wydra on 2007-11-19
Bummer, I'm running Dapper Drake, and I pdate, but I'm afraid of having to set my s\wireless up again, that was a long and painful process...

---

