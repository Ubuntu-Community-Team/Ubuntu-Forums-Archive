---
title: "USB Hard Disk"
date: 2008-09-30
forum: General Help
---

### Post by Fynn on 2008-09-30
Hi,

I've a pair of identical WD Elements 500GB hard disks that I plan to use as backup devices for my server (Hardy 8.04).  The idea is to keep one locked in my desk drawer at work and leave the other attached to the server, alternating them weekly.

I have the rsync command scheduled as a cron job and all seems to be working fine on the first disk.

Is there a way of "hot-swapping" these two disks without needing to reboot the whole system?  At the moment as soon as I unplug one I get an Input/Output error and then have to reboot in order to see it again.

Thanks in advance.

---

### Post by ryanhaigh on 2008-09-30
May seem like a silly question but are you unmounting the drives before removing them?

---

### Post by Fynn on 2008-09-30
Should've mentioned the newbie thing :-)

I tried unmount and get "bash unmount: command not found".

---

### Post by Fynn on 2008-09-30
sorry, **umount** not unmount.

better now, thanks.

---

