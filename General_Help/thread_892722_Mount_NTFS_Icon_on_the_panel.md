---
title: "Mount NTFS Icon on the panel"
date: 2008-08-17
forum: General Help
---

### Post by neur0 on 2008-08-17
I needed to setup a NTFS partition so I resized my ext3 (only) partition, and now I got:
Linux(ext3) | Extended, NTFS | SWAP

So,
When I log into Ubuntu theres an Icon on the panel like the one for the USB with which I can mount the NTFS partition, and it all works, but I don't want to be bnothered with that, I want to only be able to manually mount the NTFS one from the command line.
Don't need another Icon up in the "systray" which I will use once in a month if not rarer.

---

### Post by ajgreeny on 2008-08-17
I don't think there is any way to use Disk Mounter applet in the panel and not have it see all the disks and partitions on your machine; that's the main point of it.  It avoids you having to mount partitions at boot time using fstab, but gives you a one click way to quickly mount them when you want to.  One way to avoid the use of the Disk Mounter applet is to use a script file, with a shortcut on the panel or desktop, but I assume you don't want that either as you don't want the disk icon on the panel in Disk Mounter.

---

