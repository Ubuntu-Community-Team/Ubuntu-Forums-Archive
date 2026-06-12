---
title: "upgrading, keep home folder"
date: 2009-07-29
forum: Installation &amp; Upgrades
---

### Post by Ranko95 on 2009-07-29
Is there anyway to upgrade from ubuntu jaunty to a karmic alpha, but keep my home folder? I really hate the intel driver issues and karmic is supposed to fix that. I also wana take a look at the beautiful boot karmic is supposed to have.

Thanks!

---

### Post by Ranko95 on 2009-07-29
bump!

---

### Post by merlinus on 2009-07-29
If /home is on a separate partition, then simply choose to not format it during upgrade/install.

If not, then perhaps you can move it to one beforehand:

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by earthpigg on 2009-07-29
easiest way possible:

in the file manager, navigate to your /home/myusername/ and select view -> hidden files.

back up everything you see.

then, restore it in your new /home/myusername/, replacing the stuff already there.

---

### Post by merlinus on 2009-07-29
I agree that this is easiest, if one has a flash or external drive with enough capacity to copy everything in .mozilla-thunderbird, documents, pictures, music, and such.

And then the situation will persist when next reinstalling, or installing a newer version.

At some point, creating a separate /home partition will be best, IMFFHO, so why not now?

---

### Post by earthpigg on 2009-07-31
> **merlinus said:**
> 
At some point, creating a separate /home partition will be best, IMFFHO, so why not now?

easiest time to do *_that_* is indeed at a fresh install :D

---

