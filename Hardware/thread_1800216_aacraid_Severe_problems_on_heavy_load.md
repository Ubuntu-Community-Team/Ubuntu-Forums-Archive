---
title: "aacraid: Severe problems on heavy load"
date: 2011-07-08
forum: Hardware
---

### Post by roerich on 2011-07-08
I have 3 servers with adaptec 3405 pcie raid controller and 4 sata disks (RAID5).
OS is Ubuntu 11.04 (amd64). The servers are used for hosting VMware Server 2.0.2.

My problem: When you have heavy disk i/o on the raid (copying stuff from nfs to the server e.g.), aacraid.ko messages scsi: host adapter abort request...

I can then reboot the machine, reconstruct the array in the controller setup utility and restart Ubuntu until the controller beeps again...

Firmware is the latest - bios shows adaptec 5.2.0 17342.

Known problem? I searched google a lot but cannot find a distinct problem solution to this.

---

