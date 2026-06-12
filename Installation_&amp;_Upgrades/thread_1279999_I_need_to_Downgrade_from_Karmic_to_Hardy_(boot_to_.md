---
title: "I need to Downgrade from Karmic to Hardy (boot to initramfs after upgrade)"
date: 2009-10-01
forum: Installation &amp; Upgrades
---

### Post by malarie on 2009-10-01
Good day,

I have a Linux Server, not really used. I messed around with the apt-sources.  replaces hardy with karmic and did apt-get update.

I played a little bit with it, and i did someting wrong..  I dont know what..

Now when i reboot, Grub shows me only the Karmic Kernels, and cannot detect my software RAID  /dev/md0. It boots me to a initramfs.  I try booting with a Linux Live CD (hardy) and i cannot see the filesystems.. or any Hdds.

Anybody can point me to some doc, or can support me on how to fix the boot loader to boot back to hardy?

Or.. If its too long, I want to access my data on this RAID setup..

Thanks,.

---

### Post by malarie on 2009-10-01
Here are some information about the problem i am facing..
when i boot..

[B]Starting up....
Loading Please wait...
/scripts/init-premount/mdadm: line 98 add_mountroot_fail_hook_d not found.
Gave up the waiting for root device  Common problems:
- Boot Args (cat /proc/cmdline)
- Check rootdelay = (did the system wait long enough?
- Check Root =  (did the system wait for the right device?)
Missing Modules (cat /proc/modules; ls /dev)
ALERT! /dev/md0/ does not exists. Dropping to a shell.

Busybox v1.02 etc..

(initramfs)  _
[/B]

---

