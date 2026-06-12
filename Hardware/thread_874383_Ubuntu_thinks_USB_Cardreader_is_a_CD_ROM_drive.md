---
title: "Ubuntu thinks USB Cardreader is a CD ROM drive"
date: 2008-07-29
forum: Hardware
---

### Post by baseball116 on 2008-07-29
So, I've just recently installed Hardy on to my Asus Eee PC 701 but there is a little problem. Since I installed the distro through the cardreader (lack of optical drive), whenever an SD card is mounted it reads it as read-only. I've edited the fstab file, telling it to mount as the user with read/write and still no go. Does anyone have any ideas? Thanks in advance!

---

### Post by warp99 on 2008-07-29
> **baseball116 said:**
> So, I've just recently installed Hardy on to my Asus Eee PC 701 but there is a little problem. Since I installed the distro through the cardreader (lack of optical drive), whenever an SD card is mounted it reads it as read-only. I've edited the fstab file, telling it to mount as the user with read/write and still no go. Does anyone have any ideas? Thanks in advance!

You need to edit the file '/etc/udev/rules.d/70-persistent-cd.rules' and remove all of the entries except the comments at the top. Also remove the entries from you fstab that point to the SD card reader. Next time you reboot the udev system will read the cards as rw once you place them in the slot. Of course make sure that the SD card does not have the lock switch enabled.

---

### Post by baseball116 on 2008-08-03
I've done those exact steps (there was nothing in 70-persistent-cd.rules, just comments) and removed the card reader from fstab and it still won't let me write files to it :\ This has been confusing me for weeks now!

---

### Post by baseball116 on 2008-08-11
Anyone have any other ideas?

---

### Post by dranoweb on 2010-06-17
The fix is quite simple,

reboot, 

press f2 for bios menu

change os status to "complete" instead of "start"

---

### Post by clearwood on 2010-11-28
Yep that worked for my eee 701 :) 

But with one correction.  It's 'finished' not 'complete' instead of 'start'

Anyway thanks a hole heap :)

---

