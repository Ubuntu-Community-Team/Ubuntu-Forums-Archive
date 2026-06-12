---
title: "HD trouble preventing fresh 8.10 install"
date: 2008-11-01
forum: General Help
---

### Post by mjpatey on 2008-11-01
Hi, all!

A little background... During a dist-upgrade from 8.04 to 8.10, my system locked with "Caps Lock" and "Scroll Lock" lights on the keyboard blinking, which has been happening more and more at odd times.  The upgrade was about 2/3 through the "installing and configuring" stage, so my install was hosed.

Undaunted, I booted to a Live CD of 8.10.  I have a separate /home partition, and planned to install 8.10 on the other one, where 8.04 used to live.  Unfortunately, when attempting to install, I was told either the CD was defective (nope, it tested fine) or the hard drive was unsuitable for installation.

So I rebooted into the Live CD, and ran fsck on sdb1, the partition in question.  Here's the output (which was immediate, no delay):

```
ubuntu@ubuntu:~$ sudo umount /dev/sdb1
ubuntu@ubuntu:~$ sudo fsck.ext3 /dev/sdb1
e2fsck 1.41.3 (12-Oct-2008)
/dev/sdb1: clean, 4001/2321984 files, 207827/9277529 blocks
```

So fsck, after seemingly no checking (?) said the partition was fine, yet I still can't install.

Any ideas what to do next?  Thanks for any input!

-Mark

---

