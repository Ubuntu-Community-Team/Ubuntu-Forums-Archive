---
title: "Ubuntu not detecting HDD"
date: 2019-03-31
forum: Hardware
---

### Post by aaasixaaa on 2019-03-31
I recently made the switch from windows to ubuntu. Before switching, I was formatting my HDD and an error occurred. Now I can't find my HDD on my computer. 

Any help or advice?

---

### Post by oldfred on 2019-03-31
Any interruption of partitioning or formatting often corrupts drive.
You either have to erase partition table and start over. Reinstall & restore from backups.
Of if just format, you may be able to run fsck to repair the ext4 formatted partition(s). 

Also could be a total hard drive failure. Does UEFI/BIOS show drive in list of drives (not list of bootable devices). And are drives set for AHCI, not RAID, nor IDE, nor some sort of Intel SRT.

---

