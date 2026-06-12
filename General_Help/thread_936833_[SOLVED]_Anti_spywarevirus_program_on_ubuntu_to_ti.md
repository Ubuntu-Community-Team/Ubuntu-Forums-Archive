---
title: "[SOLVED] Anti spyware/virus program on ubuntu to tix windows"
date: 2008-10-03
forum: General Help
---

### Post by kokkus on 2008-10-03
Hi. I have some spyware in windows, so ubuntu is a great way to fix things like that.
Which program can you suggest to remove spyware, malware, virus and trojans?

---

### Post by 3rdalbum on 2008-10-03
I'm not sure whether the Linux-based anti-virus programs will deal with many forms of spyware. I've never tried any, but there's ClamAV and AVG available.

The best solution would be to erase your compromised Windows partition and either reinstall Windows or go entirely Linux. I know from experience on Windows that anti-virus programs sometimes don't get rid of the entire infection, and you can quickly become reinfected. (I had zlob.downloader - quite an annoying one that I ended off manually deleting from within Ubuntu).

---

### Post by ajmorris on 2008-10-03
> **kokkus said:**
> Hi. I have some spyware in windows, so ubuntu is a great way to fix things like that.
Which program can you suggest to remove spyware, malware, virus and trojans?

hi there,
You could try AVG or ClamAV, but if you are going to scan your windows partition with linux, and plan to have it delete/move files, make sure your windows partition is mounted with read and write access (enabled by default if you are using ntfs-3g) Also, take note, linux malware scanners tend to pick up a lot of false positives...

AJ

---

### Post by kokkus on 2008-10-03
Thank you guys:)

---

