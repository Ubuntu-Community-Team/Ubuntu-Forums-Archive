---
title: "seagate external drive says input/output error"
date: 2015-04-21
forum: Hardware
---

### Post by shankara2 on 2015-04-21
I was transferring files from my laptop (running xubuntu 14.04) to my external drive when the power died.  I can access all folders except "video" with GUI.  When I try to access the video folder I get an imput output error. I can access the video folder with the shell.  How can I resolve this issue?  Would it be easier to create a new folder and move the contents of the video folder to the new folder?

Its been years since I've used the shell extensively.

Any help would be appreciated

---

### Post by Vladlenin5000 on 2015-04-21
You have logical error in that drive due to the interrupted read/write process. The best you can do is analyze and correct the drive before anything else. Reading/writing to that drive may make the problem worse than it is now.

---

### Post by mrbigmouth502 on 2015-04-22
What filesystem were you using? If it was just ntfs or exfat, try plugging it into a Windows machine and running chkdsk /r. If it was a Linux filesystem like EXT4 or btrfs, then I'm not really sure. I could never really wrap my head around fsck. In the meantime, don't write any new data to it. Worst case scenario, you might have to look into some data recovery software, or send it into a data recovery service.

---

