---
title: "Convert FakeRAID0 to md 0+1"
date: 2009-04-02
forum: Installation &amp; Upgrades
---

### Post by TrickerZ on 2009-04-02
Right now I have a Nvidia FakeRAID0 on my system with 2 drives and I just put 2 more drives in.  Here is my setup:

/dev/sd[ab] = /dev/mapper/nvidia
/dev/mapper/nvidia1 = root
/dev/mapper/nvidia2 = swap
/dev/sd[cd]1 = /dev/md0 = root
/dev/sdc2 = /boot
/dev/sdd2 = swap

I copied my system over to /dev/md0 and can boot it as the root in fstab.  I also copied /boot to /dev/sdc2 (is there a way to make it look for /grub/stage1 instead of /boot/grub/stage1?).  I can't figure out what I need to do to grub to completely move off the FakeRAID so I can convert it to md1 and create md2 as the 0+1 array.

Please help

---

### Post by TrickerZ on 2009-04-03
For anyone that has this problem, I figured it out.  You need to create a new initrd image with mdadm in it.  I modified mdadm.conf and ran updateinitramfs -c -k <kernel-version>.  It booted my /dev/md0 and now I'm working on making my raid0+1.  Don't forget to install grub to one of your hard drives that will be booting after you get rid of the fakeraid (grub-install /dev/sdc in my case).

---

