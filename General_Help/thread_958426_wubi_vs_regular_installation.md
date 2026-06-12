---
title: "wubi vs regular installation"
date: 2008-10-25
forum: General Help
---

### Post by oaktree on 2008-10-25
Hello Exoerts,

may be this is answered before..but couldn't find an answer to this question..

What is the difference between installing Wubi Ubuntu within windows and a fresh install of Ubuntu.

Are there less features in Wubi ubuntu..or is less powerfull if not why do every body not install Wubi Ubuntu...

Thanks!

---

### Post by OneRingShort on 2008-10-25
The Wubi installer does two main things: it makes installation easier to novice users by allowing them to start the process in Windows, and select all the settings.  The second thing it does, is installs Ubuntu in a folder on the Windows partition.

Everything should the same - speed, bootloader, settings, etc... The only problem is, since its installed on the Windows partition, if something goes wrong with Windows (a probable event), and you need to reinstall, you lose Ubuntu.

---

### Post by jerome1232 on 2008-10-25
Well there's a few things, a wubi install has slower disk access times, and the file system is not as robust as a real install. (a power outage or the like can cause serious issues). Also you cannot hibernate a Wubi install.

Wubi is much easier to install and doesn't require one to partition their drive (Which can be scary for new users).

---

