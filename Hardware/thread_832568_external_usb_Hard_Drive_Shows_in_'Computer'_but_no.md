---
title: "external usb Hard Drive Shows in 'Computer' but not accessible"
date: 2008-06-17
forum: Hardware
---

### Post by nc_jed on 2008-06-17
So, I took the hard drive out of a laptop (Xubuntu / ext2), installed it to a CompUSA 2.5" portable enclosure, and plugged it in to my desktop machine (08.04).  When I go to 'Computer', the drive is there, but double-clicking does nothing.  When I right click on the icon, I see an option to mount it (clicking that does nothing also).

Ideas?

Jed

---

### Post by Odrodzona-Sarmacja on 2008-06-18
Add a line for automount for it in /etc/fstab. Then run "sudo mount -a", when you connect it after a bootup. It should mount to your wishes during bootup, if connected to computer at that time.

---

