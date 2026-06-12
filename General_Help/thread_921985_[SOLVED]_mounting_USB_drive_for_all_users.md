---
title: "[SOLVED] mounting USB drive for all users"
date: 2008-09-16
forum: General Help
---

### Post by pineapple1 on 2008-09-16
Hi,

A real newbie question... I have all my media stored on an external USB HDD. Ubuntu 8.04 does a great job of finding this and mounting it for the first user to log in anfter booting up. However, I'd like to make it available to all three users on my PC. At the moment, if i log in and use the drive for anything, then my wife switches to her login, she can't access it.

Is it possible to mount this at boot so all users can have read/write access to it?

Thx, P1 

Apologies for the double up. I originally posted this late at night and made a stupid mistake with the post title.

---

### Post by Pro-reason on 2008-09-16
You need to add an entry for it in your /etc/fstab file.

There are various documentation pages about this sort of thing, e.g. [https://help.ubuntu.com/community/MountDevicesTroubleshooting](https://help.ubuntu.com/community/MountDevicesTroubleshooting).

Hope that helps.

---

### Post by pineapple1 on 2008-09-16
Thank you, that's what I need.

---

