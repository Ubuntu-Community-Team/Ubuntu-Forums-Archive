---
title: "disk error"
date: 2006-02-10
forum: Installation &amp; Upgrades
---

### Post by tiamet on 2006-02-10
Hello, I've been trying to install 5.10 on a clean, FAT32, 30Gb hd.  It's the only disk on the system, which is an older system.
All goes well until I get to writing the partitions.  Then I get:
Input/Output error during read on /dev/ide/host0/bus0/target1/lun0/disc

ERROR ! ! !
                                 Retry
                                 Ignore
                                 Cancel

I have no idea where to begin with this and any help would be greatly appreciated.  Thanks

---

### Post by dcstar on 2006-02-12
[QUOTE=tiamet]Hello, I've been trying to install 5.10 on a clean, FAT32, 30Gb hd.  It's the only disk on the system, which is an older system.
All goes well until I get to writing the partitions.  Then I get:
Input/Output error during read on /dev/ide/host0/bus0/target1/lun0/disc

ERROR ! ! !
                                 Retry
                                 Ignore
                                 Cancel

I have no idea where to begin with this and any help would be greatly appreciated.  Thanks[/QUOTE]
Is the drive set as Slave with no Master on the IDE channel?

If so, set it to Master and see if things change.

---

