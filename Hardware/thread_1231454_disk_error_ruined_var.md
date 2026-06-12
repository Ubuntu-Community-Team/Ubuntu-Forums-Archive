---
title: "disk error ruined /var"
date: 2009-08-04
forum: Hardware
---

### Post by Xorlium on 2009-08-04
Hi,

So my laptop (Asus G50) has been working fine for about a year, running Ubuntu 9.04 now.

Today I turned it on and it gave me many error, and said "stale NFS /var ..." and things like that, and I couldn't do anything. So I started in recovery mode and it did a disk check for the root system because it had errors. It told me to do a manual check. So I did, and it fixed many inodes and cleaned stuff (I don't know what all that means, I just said yes whenever it asked me a question like "inode 812848148 should be ",," Fix(y)?")

Then I restarted, and it appears everything inside /var is broken. I couldn't even type stuff in grahpical mode. So I restarted in recovery mode again, and now I can't even start apt, because it says "could not open lock file /var/lib/dpkg/lock, no such file or directory". It says the same with many, many things that use /var. Anything I try to do fails, and it always says things like "can not open '/var/lib/mlocate/mlocate.db': No such file or Directory."

Is there anything I can do to save the system? Or will I need to do a full clean up?

Thanks!

---

