---
title: "root fs not cleanly unmounted on every shutdown"
date: 2008-08-24
forum: Hardware
---

### Post by roots on 2008-08-24
hi there,

a got a brand new ssd now running as dual boot system drive with winxp and ubuntu hardy, the latter on ext2. the ext2 partition hosts both / and a small /home. /swap is located on my hdd but never in use due to enough ram.

now there's some big annoyance here, as ubuntu cleanly unmounts my ssd-hosted file system in only like one out of ten cases.
this means, that on almost every system startup, it checks my / fs, finds errors and corrects them and after the necessary reboot, finally starts up. the drive itself seems to be fine, win is running without problems and filechecks and in general i don't see any data corruption whatsoever.

however, this should NOT be standard operating procedure, so i'm asking for suggestions and solutions here! anyone?!


thanks in advance!
.roots


some relevant system specs:

ssd: mtron pro 7535 32gb
hdd: samsung spinpoint hd322hj
controller: intel ich9 on gigabyte x38-ds5
ubuntu hardy, 2.6.24-21 kernel.

---

