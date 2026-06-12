---
title: "Move var directory to another partition"
date: 2009-11-06
forum: Installation &amp; Upgrades
---

### Post by aelorenzo on 2009-11-06
Hi all,
 
I am trying to move /var directory located in / to another partition in other disk, but when I try to boot the system with the new location for the /var directory, I get a management console because at boot the system fails trying to access to  /var/run and /var/lock (they are unavailable).
 
I have only one partition with the whole filesystem in the / directory and I would like to separate /var /tmp and /home to another disk/partition.
 
how can I get this?
 
Thanks in advance

---

### Post by jjcv on 2009-11-06
This is hard to do on a live system.   Essentially you need to do the following:

1.  copy the files from /var to your new partition:  ie  cd /var ; find . -print | cpio -pdmua /newvar

2. You then need to edit /etc/fstab to have set you newvar to be mounted as /var when your system boots.

The tricky bit is removing all the old stuff from /var before you can safely reboot.   I would suggest you boot of the install CD, then mount the ubuntu parition (may be done automatically.  Then

sudo mv /var /oldvar # (on the correct partition.
sudo mkdir /var # so there is an empty partiction to mount your newvar onto.

The after you have edited /etc/fstab you can reboot and all should be well.

Once you are happy with everything you can delete /oldvar

---

