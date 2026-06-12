---
title: "Is there a way to limit the hard drive size to avoid bad blocks?"
date: 2013-03-23
forum: Hardware
---

### Post by theplague on 2013-03-23
Hi,
I've got a 80GB hard drive that starting at 75% of its surface there are plenty of bad blocks, I created a partition that will use only 70% of the disk area just to be safe and I believe that should be ok however I was wondering if there is a program like "DD" or something else that will allow me to change the disk dimensions forever?
Thank you

---

### Post by ahallubuntu on 2013-03-23
Modern hard drives mark "bad blocks" (bad sectors) automatically in the firmware and replace them with spares.  If you check S.M.A.R.T. Attributes with GSmartControl, you'll see which ones are already reallocated (replaced with spares) and which ones are still unreadable ("pending" sectors).  Reallocated sectors are already marked "do not use" and replaced, so you do not need to do anything.  "Pending" sectors are still out there, possible landmines that will cause problems if a program tries to read from them again.  They could be anywhere on the disk, so I'm not sure why you would try messing with partitions to avoid them.

---

### Post by theplague on 2013-03-23
> **ahallubuntu said:**
> Modern hard drives mark "bad blocks" (bad sectors) automatically in the firmware and replace them with spares.  If you check S.M.A.R.T. Attributes with GSmartControl, you'll see which ones are already reallocated (replaced with spares) and which ones are still unreadable ("pending" sectors).  Reallocated sectors are already marked "do not use" and replaced, so you do not need to do anything.  "Pending" sectors are still out there, possible landmines that will cause problems if a program tries to read from them again.  They could be anywhere on the disk, so I'm not sure why you would try messing with partitions to avoid them.

Thanks for the advise, it's an old hard drive by the way and the computer won't boot if SMART is enabled on the BIOS.
I was going to give it away to a friend that needs a hard drive replacement and I just wanted to make sure that he is not going to try to use that portion of the disk with severe damage.

---

### Post by ahallubuntu on 2013-03-23
Do your friend a favor and recycle this failing drive instead of giving it to him. ;-)

---

### Post by theplague on 2013-03-23
> **ahallubuntu said:**
> Do your friend a favor and recycle this failing drive instead of giving it to him. ;-)

LOL, even better advise! :guitar:

---

