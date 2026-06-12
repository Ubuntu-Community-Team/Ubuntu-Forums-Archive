---
title: "&quot;ALERT! /dev/disk/by-uuid/&lt;uuid&gt;does not exist&quot; error after upgrading"
date: 2009-03-12
forum: Installation &amp; Upgrades
---

### Post by gravyface on 2009-03-12
Hello,

Found several posts on this subject but not getting anywhere.

I grabbed Damn Small Linux and can boot into DSL fine, but can't seem to find my hdd.
I'm pretty sure it's /dev/sda1, but fdisk -l /dev/sda returns "cannot open /dev/sda". Same for /dev/hda, /dev/hdb, /dev/sda[1-5], etc.

Bit of background:

Had an old P3 running Ubuntu 7.04 Feisty server version and did a physical to virtual migration (ESXi), which has been running flawlessly for a few weeks (had to fiddle with NICs a bit, but everything else worked fine).

Decided I should upgrade to the latest 8.10 LTS and as per Ubuntu's upgrade docs, was planning on doing an incremental upgrade to Gutsy first, using do-dist-upgrade.
Went ok until I'm assuming the kernel was updated (it asked me to restart) and am experiencing an error as described in the subject line of this thread.

Any ideas?

My GRUB menu is showing two kernels and recovery mode options, neither gets me anywhere.

---

### Post by gravyface on 2009-03-12
Resolved.  Used the Live CD and it had detected the drive and gave me the option on the desktop GUI to mount it (not sure why I couldn't with Damn Small Linux).  Had to change the root path in the /boot/grub/menu.lst to use /dev/sda1 instead of the UUID notation. Rebooted, worked.

---

