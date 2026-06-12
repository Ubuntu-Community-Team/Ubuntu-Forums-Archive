---
title: "CD/DVD drive not detected"
date: 2010-06-03
forum: Hardware
---

### Post by shrimpy89 on 2010-06-03
My laptop's CD/DVD drive has played nice with Ubuntu since the beginning, in 2008.  I've been running Lucid since it was alpha, but only recently my CD/DVD drive isn't being recognized.  When I pop a disc in, it spins up and I can hear the laser moving, but it's never detected.  Any suggestions?

---

### Post by shrimpy89 on 2010-06-08
Bump

---

### Post by gupta_sumesh63 on 2011-07-20
You do not give any clue what hardware you have. I had that problem (and suspend/hibernate issue) on an old Dell Inspiron 8200 laptop. It had a hot swap drive bay that had a DVD drive in it. But apparently because it could be hot swapped, Linux kept polling for a floppy drive, resulting in log errors attempting to read fd0, lack of auto mounting USB or CD/DVD's, and failed to suspend or hibernate because it could not put udisks-deamon to sleep, which kept polling for the non-existing floppy.

So if you have no floppy and are getting any fd0 errors in dmesg or /var/log/messages similar to "end_request: I/O error, dev fd0, sector 0", either disable the floppy in your BIOS, or if that does not work:

Add following to **/etc/modprobe.d/blacklist.conf** (use sudo or gksu to run your editor):

**blacklist floppy**

Then do: [B]sudo update-initramfs -u
[/B]
Then **reboot** and see if USB and other removable media auto mounts when inserted.

Note that other partitions on internal drives are not auto mounted unless you make proper mount points (usually in /media unless you want it mounted elsewhere) and entries in /etc/fstab (preferably using UUID). Although, they will mount if you have permission and select them in Places.

---

