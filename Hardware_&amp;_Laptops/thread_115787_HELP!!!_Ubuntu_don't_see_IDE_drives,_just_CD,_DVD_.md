---
title: "HELP!!! Ubuntu don't see IDE drives, just CD, DVD and SATA"
date: 2006-01-11
forum: Hardware &amp; Laptops
---

### Post by jkriger on 2006-01-11
Hi!
I have a FOXCONN 915P7AC-8KS motherboard with a 160G SATA drive, a CD-ROM and a DVD-ROM (both IDE) and two 40G HD (both IDE).
I installed Ubuntu on the SATA drive successfully. Ubuntu only see the CD and DVD rom, but don't see the IDE drives.

What am I doing wrong? TIA.

Regards,
Julio

---

### Post by Kipper on 2006-01-12
When you say Ubuntu doesn't see the IDE drives, do you mean the hard drives are never detected or simply that they don't appear in your file system?

Check the "dmesg" file in your logs (under /var/log) to see if the IDE drives are detected at boot time. If they are, it sounds like your /ect/fstab file has no entries to mount them at boot time.

Time for a little homework on what the mount command does, and how /etc/fstab works.

---

### Post by bentinge on 2006-05-12
I have the same problem. Ubuntu detects and installs to SATA drive, but doen't display partitions or install lilo/grup on IDE disk.

---

