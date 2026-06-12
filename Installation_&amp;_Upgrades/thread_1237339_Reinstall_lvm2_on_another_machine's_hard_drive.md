---
title: "Reinstall lvm2 on another machine's hard drive?"
date: 2009-08-11
forum: Installation &amp; Upgrades
---

### Post by cipactli on 2009-08-11
Hi, I need some help to recover from (apparently) a missing lvm2 problem... Please!

I ran aptitude yesterday on a jaunty server whose only hard drives were set up using lvm2 (well, turns out only one of the drives was alive, but that's probably secondary to this story).

aptitude said that several packages were going to be removed/consolidated, a bit later the system asked to be restarted, but it never came back: it stops in a busybox shell saying "ALERT! /dev/mapper/dev-root does not exist."

After mounting the hard drive on a jaunty desktop (nice, the machine recognized it and allowed me to mount /dev/mapper/dev-root after installing lvm2!), I realized that lvm2 itself was removed from the server (and I should have noticed that the latest kernel was being removed too! The system was back to 2.6.27-11  :(

```
Aptitude 0.4.11.11: log report
Mon, Aug 10 2009 10:35:48 -0400

IMPORTANT: this log only lists intended actions; actions which fail due to
dpkg problems may not be completed.

Will install 9 packages, and remove 21 packages.
351MB of disk space will be freed
===============================================================================
[INSTALL, DEPENDENCIES] graphicsmagick
[INSTALL, DEPENDENCIES] graphicsmagick-imagemagick-compat
[REMOVE, DEPENDENCIES] dmraid
[REMOVE, DEPENDENCIES] imagemagick
[REMOVE, DEPENDENCIES] linux-generic
[REMOVE, DEPENDENCIES] linux-image-generic
[REMOVE, DEPENDENCIES] linux-restricted-modules-generic
[REMOVE, DEPENDENCIES] lvm2
[REMOVE, DEPENDENCIES] perlmagick
[REMOVE, DEPENDENCIES] python-doc
[REMOVE] imagemagick-doc
[REMOVE] libdmraid1.0.0.rc15
[REMOVE] libmagickcore1
[REMOVE] libmagickwand1
[REMOVE] linux-image-2.6.28-11-generic
[REMOVE] linux-image-2.6.28-13-generic
[REMOVE] linux-image-2.6.28-14-generic
[REMOVE] linux-restricted-modules-2.6.28-11-generic
[REMOVE] linux-restricted-modules-2.6.28-13-generic
[REMOVE] linux-restricted-modules-2.6.28-14-generic
[REMOVE] python2.6-doc
[REMOVE] watershed
[REMOVE] wireless-crda
[UPGRADE] libapr1 1.2.12-5 -> 1.2.12-5ubuntu0.1
[UPGRADE] libapr1-dev 1.2.12-5 -> 1.2.12-5ubuntu0.1
[UPGRADE] libaprutil1 1.2.12+dfsg-8ubuntu0.1 -> 1.2.12+dfsg-8ubuntu0.3
[UPGRADE] libaprutil1-dev 1.2.12+dfsg-8ubuntu0.1 -> 1.2.12+dfsg-8ubuntu0.3
[UPGRADE] libsvn1 1.5.4dfsg1-1ubuntu2 -> 1.5.4dfsg1-1ubuntu2.1
[UPGRADE] python-subversion 1.5.4dfsg1-1ubuntu2 -> 1.5.4dfsg1-1ubuntu2.1
[UPGRADE] subversion 1.5.4dfsg1-1ubuntu2 -> 1.5.4dfsg1-1ubuntu2.1
===============================================================================


```

So, I'm guessing that the problem is that lvm2 and friends are gone from that system, but how can I recover from that? Can I somehow run aptitude on this desktop and have it install lvm2 on the server's hard drive? Or is this something that can be recovered from a Ubuntu CD?

Any pointers will be greatly appreciated!

---

### Post by cipactli on 2009-09-15
For future reference of anyone affected, it looks like this machine was affected by bug 358255:

[https://bugs.launchpad.net/ubuntu/+source/dmraid/+bug/358255](https://bugs.launchpad.net/ubuntu/+source/dmraid/+bug/358255)

---

