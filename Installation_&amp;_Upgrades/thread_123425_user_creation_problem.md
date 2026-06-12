---
title: "user creation problem"
date: 2006-01-30
forum: Installation &amp; Upgrades
---

### Post by swguru on 2006-01-30
Ok I ended up deciding to reinstall Ubuntu today, since I couldn't find any way to resize the partition it was installed on. I was able to unimstall it no problem and fix the MBR so I could single boot into Windoze again. However, I cannot get Ubuntu to install again. The problem is, when I get to the user creation step, no matter what user names or passwords I put in, it never works, and it brings up the first input in that step again (the name of the user I think). Anyone know how I can get it to stop doing this?

Edit: I forgot to say, but I did check to see if the install disk was valid, and it checked out.

---

### Post by mcduck on 2006-01-30
Are you trying to create a FAT partition as /home? That's a common reason for same kind of problems.

Also, username has to start with small letter, and you can't use any special characters in user name/password.

---

### Post by swguru on 2006-01-30
Actually I was trying to create a FAT partition, I bet that was the problem. Thanks for helping out.

---

### Post by mcduck on 2006-01-30
No problem. I hope you get your Ubuntu running now :)

FAT isn't able to store Linux file permissions and ownership, and as all your personal configurations and such are stored in your home directory, it has to be on a Linux filesystem.

If you want to share files between linux and windows, you could create a separate FAT partition for that, and mount it to /media/windows (to have icon on your desktop) or /mnt/windows (no icon). Or even /home/username/windows to have all those files inside your home directory..

---

### Post by evolvedlight on 2006-01-31
Please Sticky this, moderators. I have (hopefully soon, had) this problem. Its a bit of a trap when selecting "FAT32" and the default location is /home/. A message which detects this and prevents it in the installed (for dapper, if not for breezy?) Problems Solved! Yay

S

---

### Post by ridensnow23 on 2006-02-13
Ditto on the Sticky request.  I had to search through the Install forum for about half an hour before I came across this post.

---

