---
title: "/dev/mapper taking over windows partitions"
date: 2009-11-20
forum: Hardware
---

### Post by CorvisRex on 2009-11-20
I looked but I didn't find anything about this yet.  but.

Since I upgraded to 9.10 from 9.04, Ubuntu now lists my windows partitions (windows 7) as "dev/mapper/sil_ajadbjcfcbad1" etc.  Which I find odd.

I use two HDDs, one for Linux, one for Win. sdb is my win drive with 2 partitions.  I have NO hardware or software raid set up.  I do not use LVM. so why is the windows parts showing up in Ubuntu as part of a raid/lvm set??

I didn't worry about it before, since I don't ever access those partitions from Linux, And it didn't effect grub. But I decided to do a second fresh install of 9.10 with kde just to check it out.  But the fresh install of 9.10 rather than an upgrade, means that grub2 was installed, and this seems to really @#^%! up the grub setup.  So now I can not get into my Win7 (and before you as, i don't like it but need it for school.)

So, question is.  Why are these two partitions all of a sudden showing up as "/mapper/sil....".?  How do I stop this? 

Thanks

---

### Post by CorvisRex on 2009-11-20
Fixed...I think...I hope... Fingers crossed...

Problem seems to be that 9.10 installed dmraid, and that dmraid automatically (and incorrectly) assumed my sdb drive was part of a raid set. 

This only happened when I updated to 9.10 (did not happen in 9.04)

Nothing seemed to work until I saw something on another forum. About dmraid. 

after deleting dmraid and libdmraid from system the problem went away.  It works, but I can no longer use gparted, since the gparted package depends upon dmraid. 

now the sdb drive shows up as it should, and grub2  is functioning as it should.

---

