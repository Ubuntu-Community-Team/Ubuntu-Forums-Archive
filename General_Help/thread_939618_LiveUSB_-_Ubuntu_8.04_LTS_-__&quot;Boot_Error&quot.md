---
title: "LiveUSB - Ubuntu 8.04 LTS -  &quot;Boot Error&quot;"
date: 2008-10-06
forum: General Help
---

### Post by arkticcool on 2008-10-06
I have followed the tutorial at pendrivelinux.com to install Ubuntu 8.04 LTS onto my USB through a LiveCD installation that is persistent. I have followed all the steps exactly, and all the files and partitions have been created as stated in the tutorial. I have done this tutorial multiple times to no avail.

Whenever I boot up my USB (my computer is only 5 months old, so it supports USB booting), a message is displayed at the top which states;
```
Boot Error
```

When I press enter the normal GRUB loader appears and I can go into my normal Ubuntu installation.

I would like to know what I am doing wrong and how I can fix it. I have used the syslinux command multiple times, as stated on the website, as well as replacing the MBR with the lilo command (at the bottom of the article).

Does anyone have any idea on how to successfully load Ubuntu 8.04 LTS onto a USB persistently? I have heard of the application that can load this onto USB by itself, however both the LiveCD installer and UnetBootin don't support persistent installs.

---

### Post by arkticcool on 2009-09-13
Solved using LIVEUSB creator packaged with Jaunty.

---

