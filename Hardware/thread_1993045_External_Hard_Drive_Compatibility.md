---
title: "External Hard Drive Compatibility"
date: 2012-06-01
forum: Hardware
---

### Post by murderd2death on 2012-06-01
I'm looking to get my hands on a Seagate 2tb (STAY2000102) or a Western Digital 1.5tb (WDBAAU0015HBK-NESN). Both companies openly deny supporting linux, but I have heard people having no problems with using is as well as people who have had a hard time with them. Is there any way I can make sure that I can use these before I purchase one of them, or maybe a way i can format that drive to were it will be recognized by linux? I have a lenovo b570 laptop with 12.04 ubuntu.

---

### Post by ahallubuntu on 2012-06-01
I would think just about any external drive 2TB or smaller would work automatically in a modern Linux distro - certainly an off-the-shelf drive like the ones you mention.  I have use numerous external and portable drives in Linux and never really had any issues.

Ubuntu can handle the FAT32 or NTFS Windows formats just fine; at worst, you can just reformat a new drive with the Linux ext4 format to get the best performance with Linux.

Drives over 2TB may have issues due to the size - that's a relatively new size barrier for PCs in general, so the method of accessing them is different than before.  They may still work in Linux but I wouldn't guarantee it yet.

---

### Post by inashdeen on 2012-06-01
I have used western digital before, so i can safely say it works. not sure about seagate though. most hard disk is supported by linux, even if its fat or nfts , provided you didnt remove the nfts-3g application. the core problem is not in the hard disk itself, mostly. 

usually, hard disk provider provide extra apps like password and multiple file transfer, which only run on windows.

---

### Post by ahallubuntu on 2012-06-01
If the manufacturers claim they support Linux, then they have to answer user questions about Linux.  Say you call Seagate about a hard drive issue and call Seagate tech support.  The support person you are talking to has to then must be trained in Linux (Ubuntu? Fedora?  Which distro?).  That costs them extra money (in training) which they have decided isn't worth the investment.  Linux users will buy their drives anyway, since they mostly just work automatically.

---

