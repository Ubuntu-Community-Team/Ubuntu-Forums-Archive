---
title: "Ubuntu 19.04 stops during boot due to usb drive check failure"
date: 2019-10-04
forum: Hardware
---

### Post by bjb19592 on 2019-10-04
I have an odd situation. my system has been working fine until about a week ago. I rebooted and it failed to boot with a failure of one of my usb drives during check on boot. I made no changes to my system. If I fire up nano and mark out the fstab line for the usb drive my system boots. I can then issue the mount -a command and the usb drive mounts and functions just fine. Any ideas as to why fstab won't mount it all of a sudden?

---

### Post by sudodus on 2019-10-04
Maybe the USB drive is getting tired, and starts too slowly, so that it is not ready, when the system wants to mount a partition on it.

You can check if there are problems with the hardware using the [S.M.A.R.T. information](https://askubuntu.com/questions/972978/fsck-reports-that-filesystem-still-has-errors-what-should-i-do-now/972983#972983).

You can do it in more advanced ways using **smartctl** from the program package **smartmontools**.

---

### Post by bjb19592 on 2019-10-04
thanks, I'll give it a try

---

