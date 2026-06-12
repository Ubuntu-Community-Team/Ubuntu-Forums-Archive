---
title: "SATA Hard Drive Not Detected During Install"
date: 2005-01-07
forum: Hardware &amp; Laptops
---

### Post by chapterthree on 2005-01-07
Hello All,

Just upgrading my computer, new mobo, new SATA drive, trying to install Ubuntu, but apparently Ubuntu is not seeing the HD.  The BIOS can see the drive, but during installation, when I get to the Partition Drives section, there are no drives listed.

I tried expert mode, and it mentioned a few times that it can not load certain modules which seem to pertain to this, like IDE modules.

Any ideas?  :(

---

### Post by chapterthree on 2005-01-07
Just a follow up to this, it was an issue with the master/slave jumper on the hard drive.

On this particular drive, there were actually 3 jumper settings, Master, Master w/Slave, and Slave.  I was used to Maxtor drives, and didn't realize this drive had 3 jumper settings (instead of the 2 on Maxtor's).  It was apparently set on Master w/Slave, and that isn't kosher with SATA, it's gotta be single Master.

Yay :)

---

