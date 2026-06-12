---
title: "dosfsck - How do I update the MBR backup"
date: 2009-01-24
forum: Hardware
---

### Post by keith_is_here_2004 on 2009-01-24
Hi

I have Ubuntu 8.10.  During bootup, dosfsck (???) reports that "There are differences between the boot sector and its backup".  Then it says "Not automatically correcting this".  This is probably quite true, because I had to make changes to the CHS values in the MBR so that Partition Magic would work.  So I'd like to know how do I update this boot sector backup that it talks about?

Thanks.

---

### Post by electrogeist on 2009-01-27
I would hesitate to change CHS values on a drive without starting fresh... maybe I'm paranoid but hope you have a backup of important stuffs

you can do this to automagically try to repair everything:

sudo dosfsck -a /dev/yourFATpartition

---

