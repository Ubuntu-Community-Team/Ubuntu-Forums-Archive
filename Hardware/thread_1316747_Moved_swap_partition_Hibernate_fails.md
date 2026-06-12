---
title: "Moved swap partition: Hibernate fails"
date: 2009-11-06
forum: Hardware
---

### Post by schiotz on 2009-11-06
Hi!

I recently moved to Ubuntu (9.10 Karmic) on my laptop.  When I partitioned the harddisk, I made a small error.  A few days later, I booted on the live CD, and fixed it.  My swap partition had got a new device name (/dev/sda5), and had been moved slightly, so I ran mkswap on it, unfortunately giving it a new UUID.  After rebooting, i had to fix the UUID in /etc/fstab to get it mounted.

Now hibernate fails.  It hibernates OK, but when rebooting next time, the kernel does not notice the image in the swap partition.  Undoubtedly, it needs to be told where to find the swap partition by grub, but the new grub2 setup files are hugely complicated, and appears to be machine-written.  Can anybody points me to how I can change this, and inform grub2 about the new partition and/or the new UUID?

Best regards

Jakob

PS: It may be related: when booting, I usually get warnings printed on the boot screen about not being able to mount / and /home because something is not ready.  The UUIDs are also printed. It flashes by too fast for me to really read it, and when the system has finished booting, everything appears to be mounted correctly.

---

### Post by dv3500ea on 2009-11-06
Try:
```
sudo swapon /dev/sda
```
replace /dev/sda with the volume referring to your swap partition.

---

### Post by schiotz on 2009-11-06
Thank you very much, but the problem was not mounting the swap partition, but to read the hibernation image when linux boots after hibernating.

/Jakob

---

### Post by schiotz on 2009-11-06
Solved!  I searched in all folders under /etc for the string UUID and found the old UUID in /etc/initramfs-tools/conf.d/resume

I updated the UUID in that file, and ran "update-initramfs -u".  That fixed the problem :D

/Jakob

---

