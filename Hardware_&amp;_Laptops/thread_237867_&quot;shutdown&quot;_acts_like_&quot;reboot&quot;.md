---
title: "&quot;shutdown&quot; acts like &quot;reboot&quot;?"
date: 2006-08-16
forum: Hardware &amp; Laptops
---

### Post by christian.convey on 2006-08-16
Has anyone seen this, or knows how to fix it?...

When I shutdown my computer, it powers down but immediately starts up again, just as it would have if I'd ordered a restart rather than a shutdown.

I'm running Dapper on a desktop computer that has an Athlon64 processor.  My motherboard is a Gigabyte GA-K8NF-9 (nForce board) with an Award BIOS.

The funny thing is, the computer shuts down properly under Knoppix 5.01 (the current one) and Windows.

Note: I'm also seeing this with the current builds of Edgy Eft.

Any ideas?

Thanks,
Christian

---

### Post by wpshooter on 2006-08-16
Has it been doing this consistently ever since you installed Ubuntu or did it start sometime after the installation of Ubuntu ?

---

### Post by christian.convey on 2006-08-16
Consistent.  I think it goes back to Breezy as well.  Breezy, Dapper, Edgy, and Knoppix are the only distros I've run on this computer.

---

### Post by christian.convey on 2006-08-16
I fixed it.  I finally updated the BIOS from a 2004 version to the current 2006 version, and the problem went away.

It still seems a little odd that Windows/Knoppix handled it ok even under the old BIOS version whereas Ubuntu needed the new BIOS version.  But either way I'm just happy it works.

---

### Post by wpshooter on 2006-08-17
Glad you got it fixed.

A lot of folks go by that old theory that "if it ain't broke, don't fix it".  But in my opinion the people that manufacturer these computers would not write BIOS updates if there wasn't something broken.  And if you don't keep your software up-to-date, it can be broken and you don't even know it.

---

### Post by gerry2k5 on 2006-10-05
I have the same problem with an iMac G3.  Shutdown works fine in OS 9 and OS X, but with Dapper, the system always restarts when I choose shutdown.  Does anyone have any suggestions?

---

