---
title: "terrible 3D performance for ATI 9800 XT"
date: 2010-01-21
forum: Hardware
---

### Post by Eirinjas on 2010-01-21
Like the title says, my video performance is awful.  Some games won't run, and those that do chug.  Urban Terror crashes half the time on exit, but it's unplayable anyway because the framerate dips so low and textures flicker.  

Any help would be greatly appreciated.

---

### Post by DRF on 2010-02-02
There seems to be a common problem many people are having with the radeon module loading before the agp modules. There is a bug report logged [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/468413](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/468413)

For me opening a terminal and typing:
sudo rmmod radeon
sudo modprobe radeon
sudo /etc/init.d/gdm restart

fixes this for that session until I next restart the computer (the last line of above will take you back to the logon screen so save any work before cutting and pasting to a terminal window). If this doesn't help you might be experiencing a different issue.

Daniel

---

