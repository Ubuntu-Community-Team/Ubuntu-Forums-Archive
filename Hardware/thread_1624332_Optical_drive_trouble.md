---
title: "Optical drive trouble"
date: 2010-11-17
forum: Hardware
---

### Post by Buntumatic on 2010-11-17
I installed latest Lubuntu for a friend of mine, an oldish HP Pentium 4.
Install worked from CDR.

But from installed Lubuntu all I get is "Media not present" or similar message, no matter what media I put in. Both optical drives act the same. 
Kernel recognizes the drives, udev creates nodes. Both nodes belong to root:cdrom and my user is in cdrom group.
That makes me think it has something to do with kernel configuration.

Has anybody experienced similar problem? I'd build a custom kernel but I don't think it's a good idea on distro which has automatic kernel updates.

---

### Post by Buntumatic on 2010-12-19
> **Buntumatic said:**
> But from installed Lubuntu all I get is "Media not present" or similar message, no matter what media I put in. Both optical drives act the same. .
Correction. Some media is recognized and read.
I'm starting to think HP has non-standard proprietary firmware in these drives. For instance, Xfburn detects DVD writer as HP DVD Writer, yet it displays drive is not capable of writing DVD's. (It is indeed, this computer had Windows installed before and DVD's were burned.)

Can anyone confirm such a hardware/firmware incompatibility may exist so I can stop troubleshooting and recommend buying a new drive?

---

### Post by IcarusR on 2010-12-19
Does it fail on pre-recorded madia & self burnt ?
Some drives are fussy on recordable media.
Try cleaning the laser lens carefully.

What make & model of writer is it ?

What do the log files say when it fails to read disc ?

---

### Post by Buntumatic on 2010-12-19
So far it only works with CDR, fails on DVDR (which are burned with same drive under Windows), DVD, CD. 
I tried with audio CD and it was able to get the number of tracks but failed to open them.
I did not look into /var/log/messages, my mistake. Mostly it gives (depending on app used) errors like "cannot read device" or "media not found".

Both drives are branded HP, both behave the same. If I knew the real manufacturer I'd try and flash them.

Unfortunately I do not visit this friend of mine very often, it's a 70 mi round trip.

Hmmmm ... now when I think of it I recall having similar problem once before ... Windows worked fine and Linux had trouble. Turned out jumpers were not set correctly. 

Thanks for reply. :) Will investigate this further when I get a chance.

---

