---
title: "Can't access USB stick anymore"
date: 2007-10-14
forum: Hardware &amp; Laptops
---

### Post by DalekClock on 2007-10-14
I'm trying to get to a document on my USB stick. Recently I got a spontanious message saying "Removable media removed without Eject" or something, and now I cant' access my USB stick at all. It shows up in Hardware Information, but I can't find it in Nautilus.

What now?

---

### Post by Linicks on 2007-10-14
If you removed it while the system writing to it, you could well have trashed the stick's file system so it is now unreadable.  From my experience with users at work, it is now dead.

This *can* happen in any OS if you remove it in these circumstances.

Nick

---

### Post by DalekClock on 2007-10-14
See that's the thing, I didn't remove it and have no idea why I got the message.

---

### Post by 5-HT on 2007-10-14
Uh oh...looks like the drive may have been physically removed during write.
Check out dmesg after inserting the drive to see if anything pertinent comes up. Have you tried manually mounting? Also would be a good idea to check the filesystem as it could be corrupted.
cheers,

[edit, a little late] The above still applies though, no matter the cause.

---

### Post by DalekClock on 2007-10-14
How do I do any of those?

---

### Post by DalekClock on 2007-10-15
Well, now it seems to find the stick, but I can't find any of the files. This is after I tried accessing it on my Windows partition.

---

