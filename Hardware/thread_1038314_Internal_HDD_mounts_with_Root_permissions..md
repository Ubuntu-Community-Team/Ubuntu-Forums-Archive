---
title: "Internal HDD mounts with Root permissions."
date: 2009-01-12
forum: Hardware
---

### Post by Benkrishman on 2009-01-12
I just put a new SATA HDD in my ubuntu 8.10 desktop.  After formatting it ext3 I mounted the drive and attempted to move some files to it but was told that I needed root permission to write to the drive.

Can anyone tell me how to make my drive mount with read/write permissions for normal users?  Also, how can I get the drive to automount when I start up?

---

### Post by logos34 on 2009-01-12
you need to chown and chmod it, and add it to fstab:

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

