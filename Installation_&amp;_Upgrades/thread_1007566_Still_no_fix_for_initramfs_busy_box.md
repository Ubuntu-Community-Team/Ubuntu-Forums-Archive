---
title: "Still no fix for initramfs busy box?"
date: 2008-12-10
forum: Installation &amp; Upgrades
---

### Post by geminiviper on 2008-12-10
Is there a solution to running into the initramfs busy box yet?  I have been digging and trying and digging some more to figure out why I can install *Ubuntu 8.* from a live cd or from the main installer ap but once I reboot all I get is the scrolling bar back and forth for a few minutes then [initramfs].  I cannot seem to get out of that screen to see what's going on either...  I'm a bit newer to Linux but not a complete newb, still new enough I don't understand a few things or don't know that option existed.  

I have posted about this problem before, and as I see so many other people have too, and like me they rarely get a response.  Is there anyone who can help with this or are we just stuck with an older version, a different distro or waiting for the next version?

---

### Post by abn91c on 2008-12-10
at the initramfs prompt wait a few seconds then type exit and hit enter see if anything happens

---

### Post by Zorael on 2008-12-10
When I had BusyBox prompt issues they were caused by having erroneous UUID entries in /boot/grub/menu.lst and /etc/fstab. I changed them to point to device nodes (/dev/sdxy), after which stuff worked again. Somehow, along the road, my filesystems' UUID values were changed, causing it to fail to mount them upon boot. No root fs = BusyBox prompt.

```
$ sudo blkid
```

---

### Post by bsmith1051 on 2008-12-11
> **Zorael said:**
> No root fs = BusyBox prompt.
This is exactly right.  If you can figure-out how to mount your drive from the command-line, then type 'exit', everything will work correctly.

For instance, this is what happens if you have RAID (duplicate drives) setup and one of the drives fails.

The more common reason is your /etc/fstab configuration file is incorrect, e.g. the partitions are specified by UUID instead of device name.

---

