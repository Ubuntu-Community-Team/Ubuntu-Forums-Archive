---
title: "Windows access to linux file system"
date: 2009-02-12
forum: Installation &amp; Upgrades
---

### Post by davidself1001 on 2009-02-12
I loaded the driver (ext2 ifs) for Windows that allows it to access my linux drives.  When I try to access the drives I get a request to format them.  In the FAQ it indicated that I needed to run the mountdiag, which I did.  It says that the inode size is 256 on the linux drives and it needs to be 128.  How do I change that?  Can it be done without reformatting the disks?

---

### Post by davidself1001 on 2009-02-12
Ok, is this a dumb question or have I stumped everyone?

---

### Post by marshimaro on 2009-02-13
how about explore2fs?
[http://www.chrysocome.net/explore2fs](http://www.chrysocome.net/explore2fs)

---

### Post by davidself1001 on 2009-02-13
Thanks.  I'll give that a try tonight.

---

### Post by InfectedWithDrew on 2009-02-19
Hello, the same problem was affecting me.

This explore2fs program doesn't work, the 1.08 beta reads some hda5 which I DON'T have and the 1.07 reads hdb1 which contains nothing.

So it's really a problem of, during installation, setting the inode size to 128 instead of the default 256.

---

