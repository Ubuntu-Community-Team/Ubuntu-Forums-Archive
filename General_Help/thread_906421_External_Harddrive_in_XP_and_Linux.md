---
title: "External Harddrive in XP and Linux"
date: 2008-08-31
forum: General Help
---

### Post by yousillygoose on 2008-08-31
I have external hard drives that I want to be able to use in both windows and linux.  I was wondering which of 2 options would be better: formatting to ntfs and using ntfs-3g in linux or formatting to fat32 and taking the efficiency loss.  I have never used ntfs-3g and didn't know how flawed it was (if at all) and if it runs safely.  Any help is always appreciated.

ysG

---

### Post by coffeecat on 2008-08-31
You don't say which version of Ubuntu you are using, but if it's 8.04 then my experience has been that NTFS read-write works out of the box with ntfs-3g and reliably. So much so that I've converted my main USB drive to NTFS as well as the shared data partition for Windows and Linux on an internal drive; I used to use FAT32.

The only potential problem I can see with NTFS is that if you suffer an unclean unmount with it and the journal needs recovering, you probably need to do this in Windows. I realise that there are several utilities that come with ntfsprogs, but I don't believe they can cope with all situations. I would be happy to be corrected, though.

---

### Post by yousillygoose on 2008-08-31
that is a response that makes me happy.  I would much rather do ntfs than fat32.  I will start the format!  More posts thought o reassure or change my mind!

---

### Post by Sycron on 2008-08-31
You can see ext2/3 partitions in Windows with ext ifs [www.fs-driver.org/](www.fs-driver.org/) .

---

### Post by yousillygoose on 2008-08-31
I want to be able to use it in both os's fluently

---

### Post by toolisima on 2008-09-13
Hey, I just got an external hard drive and need to format it, and also be able to use it in both Ubuntu (7.04) and Windows Xp...Im a beginner though, so if anyone here can actually tell me the how to it'd be great!
Thanks!

---

### Post by Sycron on 2008-09-15
You have to partitionate your hard-drive. You can use gparted livecd or Ubuntu live cd for that purpose.

---

