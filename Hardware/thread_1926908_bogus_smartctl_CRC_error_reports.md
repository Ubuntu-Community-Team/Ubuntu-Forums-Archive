---
title: "bogus smartctl CRC error reports?"
date: 2012-02-17
forum: Hardware
---

### Post by akos.maroy on 2012-02-17
Hi,

I encountered a strange issue recently. smartctl started to list CRC errors on two of my (similar) HDDs. I ran the extended test several times, and each time the CRC error count increased.

So I took the HDDs back to the store for a warranty replacement, but when they looked at it, they said they are not finding problems, with SMART or otherwise. I told them to look further, then they ran the DOS-based Hitachi error checking software, and that didn't find errors either.

So I got back the HDDs, with smartctl still listing the very same errors. but, for example if I start the ubuntu Disk Utility, that is not showing any errors, even after running the extended test again. I booted in to Windows and try to look at the drive there as well, but it doesn't report any issues either.

Now I'm doing a full dd if=/dev/urandom of=/dev/sdc bs=1m on the drive to see if this fails anywhere, which would indicate a hardware issue. this has completed to about 1/3 of the drive so far, with no errors so far - will see if it completes for the whole drive w/o errors.

but, I wonder what the cause of the discrepancy could be between smartctl reporting CRC errors, but other tools not, like the ubuntu Disk Utility?


Akos

---

