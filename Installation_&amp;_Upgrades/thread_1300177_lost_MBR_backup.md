---
title: "lost MBR backup"
date: 2009-10-24
forum: Installation &amp; Upgrades
---

### Post by meetquant on 2009-10-24
I had a dual-boot system with Vista and Ubuntu. To install XP in place of Vista using XP CD, I had to zero MBR. I backed-up MBR using 'dd', however on the same system, wriring to /home/someuser/mbr.backup !! really stupid.

I have failed to installed XP, but horrible thing is now my partition table is lost, and I cannot access the file system (I cannot get to the backed-up MBR to restore it). I tried 'testdisk', and was able to recover most  vista and other data partitions, however not the main linux file system (it says it's corrputed ). However that partition is most important to me!!

Please tell me how I can recover that partition and get the system to boot from ubuntu. (the exact MBR should be still there in that partion once I get access to it.)

Please help me. Thank you very much.

---

