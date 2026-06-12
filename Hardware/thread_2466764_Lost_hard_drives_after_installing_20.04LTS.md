---
title: "Lost hard drives after installing 20.04LTS"
date: 2021-09-05
forum: Hardware
---

### Post by dlwy3k on 2021-09-05
Have 18.04 and 20.04 installed. Installed 20.04 along side of 18.04 so not to loose data in 18.04.
However, two of the three hard drives do not show up in 20.04. Gparted nor the BIOS list them either.
Neither does fdisk.
How is this solved?

---

### Post by TheFu on 2021-09-05
Just some ideas ....

If the BIOS doesn't see them, then the OS won't either.  Perhaps a firmware update to the drives is needed / or the BIOS?  This is common for SSDs using NVMe interfaces.  If it is for SATA HDDs (spinning disks), then check the cables and power.

If you don't want to loose data, have a disconnected backup.

Do you use standby or hibernate?
File systems that are left open, can't be accessed.  This is normally a Windows fast-start thing.  I've not seen it with Linux, but I don't multi-boot any of my systems.  That's what virtual machines and linux containers are for around here.

---

