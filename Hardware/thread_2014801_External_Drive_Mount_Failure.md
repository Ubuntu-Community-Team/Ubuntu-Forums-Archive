---
title: "External Drive Mount Failure"
date: 2012-07-02
forum: Hardware
---

### Post by cozski on 2012-07-02
I have inserted an 8GB Ativa Flash Drive but in Disk Utility I get this message:

**Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sdc1, missing codepage or helper program, or other error. In some cases useful info is found in syslog - try dmesg tail or so**

I'm not sure what to do at this point so any advice/info would be appreciated.

Thanks.

---

### Post by sudodus on 2012-07-02
It could be the new and proprietary file system exFAT, that is not read by standard linux. But there are drivers to download for it.

It could also be something wrong with the pendrive, bad hardware, corrupted partition table or file system.

If you have or can borrow a Windows computer, try it there, and check if it works, and in that case, what is the file system!

You can also follow the route suggested in the error output: 'In some cases useful info is found in syslog - try dmesg tail or so'

---

### Post by cozski on 2012-07-02
I stuck it into a Windows PC and it said it was Fat32 from what I could gather (not quite my area of expertise). I then formatted it too Ext4 and it has no mounted in my Ubuntu OS no problem. Thanks for reply.

---

### Post by sudodus on 2012-07-02
> **cozski said:**
> I stuck it into a Windows PC and it said it was Fat32 from what I could gather (not quite my area of expertise). I then formatted it too Ext4 and it has no mounted in my Ubuntu OS no problem. Thanks for reply.

Fine, you are happy with ext4 (you are not going to use it with Windows) :KS

But actually, a healthy FAT32 system can be read/written by Ubuntu, so I guess there was something wrong with it. Maybe it would have worked with a simple ```
chkdsk /f
``` in Windows to get it readable also in Ubuntu.

If you feel that your problem is solved, please click on ```
Thread Tools
``` at the top of this page and mark this thread as SOLVED.

---

