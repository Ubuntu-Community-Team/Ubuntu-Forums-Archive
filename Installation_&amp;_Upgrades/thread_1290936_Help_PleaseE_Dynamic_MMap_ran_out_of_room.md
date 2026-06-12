---
title: "Help Please:E: Dynamic MMap ran out of room"
date: 2009-10-14
forum: Installation &amp; Upgrades
---

### Post by jokerqiang on 2009-10-14
Hi, when I try to start package manager, I got following error, and the package manager can not be started.
E: Dynamic MMap ran out of room
E: Dynamic MMap ran out of room
E: Error occurred while processing mrxvt-cjk (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/tw.archive.ubuntu.com_ubuntu_dists_hardy_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

anyone can help, this is really disaster  for me:confused:

---

### Post by bruno9779 on 2009-10-14
```
sudo apt-get autoclean
``` should do the trick temporary

To avoid having the same issue again you should raise the apt cache limit.

[here]("http://www.linuxquestions.org/questions/debian-26/dynamic-mmap-ran-out-of-room-error-when-adding-new-apt-source-list-233417/")

---

### Post by jokerqiang on 2009-10-14
Thanks,
After raise cache size, I got following error:

tiger@tiger-laptop:~$ sudo apt-get autoclean
Reading package lists... Error!
E: Wow, you exceeded the number of versions this APT is capable of.
E: Problem with MergeList /var/lib/apt/lists/ftp.tw.debian.org_debian_dists_lenny_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.


Help please :confused:

---

