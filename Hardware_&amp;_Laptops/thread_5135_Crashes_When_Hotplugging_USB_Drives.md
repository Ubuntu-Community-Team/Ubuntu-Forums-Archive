---
title: "Crashes When Hotplugging USB Drives"
date: 2004-11-15
forum: Hardware &amp; Laptops
---

### Post by talkingwires on 2004-11-15
Hi, I'm new!

Quick History:
I recently switched over to Ubuntu from Debian. I'd been running Sid for a while, but wanted a distro that didn't seem to be fighting new technology tooth and nail. (Stable runs a 2.4 kernel, and even in Sid Udev, ALSA, or X.org are missing or disabled by default.) I spent weeks working to get a USB flash drive to hotplug and automount, and ended up with something that sortof worked, provided you never unmounted it or ever wanted to mount your CD or DVD drives again.

The Problem:
So far I've been pretty impressed with Ubuntu (I just got X.org and hardware compositing running smoothly :grin:). But I'm still having trouble with my USB flash drive. Anytime I try to hotplug it, my USB mouse dies and the drive never mounts. If I plug it in before I boot, it usually shows up on my desktop twenty seconds or so after I log in. During boot, right after the hotplug module is loaded, I see a brief message about loading pciehp and shpchp not being permitted, if that helps. I'd really like to get this working, as it's kind of a deal-breaker. Has anyone else had problems like this? Which log files would be helpful? Thanks!

---

### Post by bazuka on 2004-12-04
[QUOTE=talkingwires]Hi, I'm new!

Quick History:
I recently switched over to Ubuntu from Debian. I'd been running Sid for a while, but wanted a distro that didn't seem to be fighting new technology tooth and nail. (Stable runs a 2.4 kernel, and even in Sid Udev, ALSA, or X.org are missing or disabled by default.) I spent weeks working to get a USB flash drive to hotplug and automount, and ended up with something that sortof worked, provided you never unmounted it or ever wanted to mount your CD or DVD drives again.

The Problem:
So far I've been pretty impressed with Ubuntu (I just got X.org and hardware compositing running smoothly :grin:). But I'm still having trouble with my USB flash drive. Anytime I try to hotplug it, my USB mouse dies and the drive never mounts. If I plug it in before I boot, it usually shows up on my desktop twenty seconds or so after I log in. During boot, right after the hotplug module is loaded, I see a brief message about loading pciehp and shpchp not being permitted, if that helps. I'd really like to get this working, as it's kind of a deal-breaker. Has anyone else had problems like this? Which log files would be helpful? Thanks![/QUOTE]
 You know, I had a similar problem with getting my USB drive to work in OS X. I went to my windows box and did this:
> format f: /FS:FAT32 /X /A:8192
After that, it worked without problems. I don't know what it is about some thumbdrives, but they need some extra work before they're actually cross-platform friendly.

---

### Post by kmoz on 2004-12-07
I'm experiencing a similar problem.  When I first installed Ubuntu, my Lexar Jumpdrive would automount perfectly, but refused to unmount.  Then I edited the fstab entry to:

/dev/sda1       /media/jump     vfat    rw,user,noauto  0 0

which seems to result in the system crashing (screen freeze, can't ctrl-alt-F2 to prompt) when the device is plugged in.  One of the posts here mentioned that it's a kernel issue with a usb 2.0 drive being plugged into a non usb 2.0 port, but that doens't explain why mine used to work.  I'm going to try removing the fstab setting and see if it reverts back to normal.  In the mean time, is there a way of removing this automount feature?  I don't mind mounting through fstab and a terminal...

---

