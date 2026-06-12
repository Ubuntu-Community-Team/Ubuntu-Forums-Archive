---
title: "Incomplete booting after installation"
date: 2005-12-18
forum: Installation &amp; Upgrades
---

### Post by cnolanAU on 2005-12-18
I've just finished an apparently successful install, but after reboot, my machine tries to boot, and ends up in a shell with what looks like just the ramdisk mounted.  I'm using LVM with ReiserFS, except my /boot partition which is a primary ext3 partition.  It fails just after it starts loading /dev, the messages I see before it drops to a prompt are:

/scripts/local-top/evms: 31: /sbin/evms_activate: not found
Done.
Begin: Running /scripts/local-premount ...
[4294679.093000] Attempting manual resume
[4294679.093000] swsusp: Suspend partition has wrong signature?
Done.
FATAL: Module unknown not found.
mount: Mounting /dev/root on /root failed: No such device
Begin: Running /scripts/local-bottom ...
Done.
Done.
Begin: Running /scripts/init-bottom ...
Done.
mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory
mount: Mounting /dev on /root/dev failed: No such file or directory
Target filesystem doesn't have /sbin/init

Anyone have any ideas what's gone wrong here?

Cheers,
Chris.

---

### Post by cnolanAU on 2005-12-19
Well, I reinstalled, and got a different message when it came to the grub installation section (found other operating systems, and asked if I wanted to install grub in MBR, rather than just asking me which partition I'd like to install grub).  I went ahead with the MBR installation, and all is well now.  I've no idea what went wrong the first time around.

Cheers,
Chris.

---

