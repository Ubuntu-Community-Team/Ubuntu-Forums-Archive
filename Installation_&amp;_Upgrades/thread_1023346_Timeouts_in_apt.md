---
title: "Timeouts in apt?"
date: 2008-12-27
forum: Installation &amp; Upgrades
---

### Post by sci-fi guy on 2008-12-27
My ISP likes to kill transfers of large files, and my only option is to restart the download. I have moved all my repository listings to ftp, so the downloads pick up where they left off, but I still need to babysit the connection so that I can restart it when it quits.

How can I get apt to automatically time out and resume the connection after it has been stalled for a few seconds?


EDIT: And while I am asking, is there any way to force apt to download multiple files in parallel rather than serial?

---

### Post by polmir on 2008-12-27
Type in terminal:```
man apt
man apt-get
man apt_preferences
man apt.conf
man apt-config
```and try to look for something in these instructions.

---

