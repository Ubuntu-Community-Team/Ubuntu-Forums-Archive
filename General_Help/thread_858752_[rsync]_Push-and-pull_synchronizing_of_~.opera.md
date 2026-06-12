---
title: "[rsync] Push-and-pull synchronizing of ~/.opera/"
date: 2008-07-13
forum: General Help
---

### Post by Aleksandersen on 2008-07-13
Hi all,

I have a question about rsync[d]. I have Windows and I have Debian on the same machine, running from two partitions. The two never run at the same time.

I use the Opera web browser on both operating systems. I would like to synchronize the two profiles ~/Application Data\Opera\Opera\profile (Windows) and ~/.opera/ (Linux). Since Windows sucks and I rarely use it, I think running the synchronization process from Linux only will suffice.

I think this should work, but I do not know how to set it up: From Linux, I will run a rsync daemon that will pull updated files from the Opera profile on Windows, and push files that are more recent on Linux to Windows. A short exclusion list would also be needed.

PS: Monting ext3 on Windows and NTFS on Linux is not a problem.

How do I set this up? :-)

---

