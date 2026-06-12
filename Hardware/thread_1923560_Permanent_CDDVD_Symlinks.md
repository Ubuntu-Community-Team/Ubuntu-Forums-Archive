---
title: "Permanent CD/DVD Symlinks"
date: 2012-02-10
forum: Hardware
---

### Post by Sith Lord Kyle on 2012-02-10
I have a system with multiple optical drives in it and I'm trying to keep them under the same symlinks, and/or mount-points.

I have tried mounting them with fstab but, upon each reboot, the mount-points correspond to different drives.  Also when Ubuntu starts up, it gives me a mount error, though when skipped it seems to mount the drives.

I tried writing udev rules, but those also seem to change with each reboot.

Is there a way to make, say, the top optical drive symlink to sr0 permanently?  Second drive to sr1, etc.

Hopefully I'm explaining this well enough someone will understand it.

---

### Post by brpylko on 2012-02-10
as long as no hardware is changed between each reboot they should correspond to the same device each time (due to the order that they are loaded by the kernel, I think this has something to do with each one's IRQ#, not sure though)

---

### Post by Sith Lord Kyle on 2012-02-10
Yeah, there aren't any hardware changes taking place that I can tell.  They are just dvd-roms.  But for some reason the symlinks and mount points change each reboot.  If it is an IRQ, how do I work around it, I wonder.

---

### Post by Sith Lord Kyle on 2012-02-15
I noticed if I remove the Fstab records for these drives, they will go back to a set version of the sr0 symlinks... but if I use Fstab, those all change.  I tried writing udev rules, but those also change every reboot.

---

