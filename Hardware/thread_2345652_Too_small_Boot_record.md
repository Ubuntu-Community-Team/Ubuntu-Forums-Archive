---
title: "Too small Boot record"
date: 2016-12-06
forum: Hardware
---

### Post by rgammon51 on 2016-12-06
Ubuntu 16.04.1 installed.  It created a boot record of 255MB which too small for updates  The system is otherwise LVM2

Check for answer tomorrow

---

### Post by rgammon51 on 2016-12-06
Reinstalling does not seem to be the answer I am looking for

---

### Post by oldfred on 2016-12-06
With 16.04, they now automatically will remove all but 2 kernels. Previously many users had issues like yours.

The only other choice is to partition in advance and manually install. 

Do you run this?
sudo apt-get autoremove


       /boot full or Not enough disk space on updates
[http://ubuntuforums.org/showthread.php?t=2308938&p=13418808#post13418808](http://ubuntuforums.org/showthread.php?t=2308938&p=13418808#post13418808)
[https://help.ubuntu.com/community/RemoveOldKernels](https://help.ubuntu.com/community/RemoveOldKernels)

---

