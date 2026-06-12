---
title: "What is the partition name in Wubi for the boot disk?"
date: 2008-09-22
forum: General Help
---

### Post by MockY on 2008-09-22
I installed Ubuntu for a friend of mine using Wubi, something I usually don't do. I installed Hardy Heron and a know bug is causing clicking sounds of the hard drive. I found a solution for it but the problem is, the hard drive is not listed as /dev/sda anymore like it usually do when installed the regular way.

fstab is listing it as /host/ubuntu/disks/root.disk and I am unsure if I should replace /dev/sda with this.

The guide I am following is found here:
[http://www.actionshrimp.com/2008/05/laptop-hard-drive-clicking-in-hardy/](http://www.actionshrimp.com/2008/05/laptop-hard-drive-clicking-in-hardy/)

Help is much appreciated.

---

### Post by ago on 2008-09-23
The real device is the one which is mounted as /host

grep /host /proc/mounts

---

