---
title: "Problem adding third IDE drive"
date: 2007-03-20
forum: Hardware &amp; Laptops
---

### Post by Zyyke on 2007-03-20
Greetings form Norway!

Somewhat of a linux noob here, but have recently configured my own mediaserver with SMB and shared HP Laserjet 1018 reading the tutorials and forums here. But a new problem got me stumped. I just added a third drive to my Ubuntu 6.06 setup. 

Current configuration is as follows:
- 1st IDE controller: 2 x IDE drives, jumpers set at master and slave
- 2nd IDE controller: 1 x DVD drive (jumper set as master) and 1 x IDE drive (jumper set as slave).

The drives are recognized correctly as hda-hdb-hdc-hdd, added to /etc/fstab and mounted.
So far so good.

But when trying to copy files from hda-hdb-hdc to hdd, the system locks up.
Tried removing the DVD-drive, and setting hdd as master and hdc, but same results.

Anyone have any input on what the cause of this could be, or how I can work out what the problem is? Might this be a problem with Ubuntu? Or the second IDE controller?

---

### Post by apjone on 2007-03-23
Have you formatted the drive etc?

---

### Post by Zyyke on 2007-03-24
> **apjone said:**
> Have you formatted the drive etc?

Sure. Drive is formatted, partitioned and mounted. Can access and copy files to, but as soon as  try to do a large file copy to the drive, the machine locks up. Is this a probable software error (anyone experienced similar) or might it be the IDE cable or controller?

---

### Post by Zyyke on 2007-03-27
bump

---

