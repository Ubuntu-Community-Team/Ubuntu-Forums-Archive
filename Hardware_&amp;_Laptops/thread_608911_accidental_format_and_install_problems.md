---
title: "accidental format and install problems"
date: 2007-11-10
forum: Hardware &amp; Laptops
---

### Post by santaandy on 2007-11-10
Okay, here goes:

I was running Vista and installed alcohol 120, got locked into a bsod/reboot sequence.  Installed ubuntu on main drive (same as vista) with guided install.  Now, I cannot access my old data from windows desktop.  Is my data totally and completely gone forever?  I thought as long as hard disk was not physically damaged data is always possible to recover.  Was the data overwritten by linux?  Had 20gb free before install, most data just programs which are easy to reinstall.  Thankfully, if all is lost nothing important was lost.  However, would be nice to recover.

Thanks

Andy

---

### Post by cubeist on 2007-11-10
> **santaandy said:**
> Okay, here goes:

I was running Vista and installed alcohol 120, got locked into a bsod/reboot sequence.  Installed ubuntu on main drive (same as vista) with guided install.  Now, I cannot access my old data from windows desktop.  Is my data totally and completely gone forever?  I thought as long as hard disk was not physically damaged data is always possible to recover.  Was the data overwritten by linux?  Had 20gb free before install, most data just programs which are easy to reinstall.  Thankfully, if all is lost nothing important was lost.  However, would be nice to recover.

Thanks

Andy

Well, if you didn't specify a separate partition during install, then like most installers it used the largest contiguous free space... which would have been your only partition...windows... basically I think you wrote over your data...  If you want to be sure, add a program called gparted and that will show you all the partitions on your hd.

---

### Post by Mondoman on 2007-11-10
> **santaandy said:**
> ...I thought as long as hard disk was not physically damaged data is always possible to recover. ...
No, if it's been overwritten, at best it's extremely difficult to recover.

---

