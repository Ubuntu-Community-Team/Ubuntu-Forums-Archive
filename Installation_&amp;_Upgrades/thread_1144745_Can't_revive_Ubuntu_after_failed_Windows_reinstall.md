---
title: "Can't revive Ubuntu after failed Windows reinstall"
date: 2009-05-01
forum: Installation &amp; Upgrades
---

### Post by JusticeZero on 2009-05-01
My laptop uses a Windows dual boot, and Windows imploded. I got a CD to reinstall it, but it seems to not be the right CD as it won't accept the license key. So I booted up off of a boot CD and tried to get Grub back in place.
```
grub> root (hd 0,0)

Error 23: Error while parsing number

grub> root (hd0,0)

grub> setup (hd0)

Error 17: Cannot mount selected partition
``````
ubuntu@ubuntu:~$ mount hd0
mount: can't find hd0 in /etc/fstab or /etc/mtab
```
My Ubuntu partition seems to be in media/disk; my programs in media/disk-1, and my data in media/disk-2. I'd kind've like to not have to revert to a backup of my data, as that would lose quite a bit of the stuff I was working on recently. For some reason, the boot CD seems able to see my external hard drive, but not to be able to write to it, even on the ext3 partition. Suggestions?

---

