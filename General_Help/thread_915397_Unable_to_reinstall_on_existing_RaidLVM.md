---
title: "Unable to reinstall on existing Raid/LVM"
date: 2008-09-09
forum: General Help
---

### Post by thebrandons on 2008-09-09
On my initial install I utilized the Alternate CD to create the following setup.  Two 500GB HDs were set up as Raid 1 and then 2 partitions were created.  One partition used for /boot and the other for LVM.  On LVM all the standard mounts exists (ie. /usr, /swap, etc).  Everything worked until I needed to reinstall for a separate issue.  I repeatedly tried the following approaches without success.

1) Simple reinstall using existing RAID partitions and LVM.
The partition section of the install did not show the RAID MD devices.  When I selected “Configure Raid” the md0/md1 already existed so I hit finished.  Next I received a message indicating that a “reboot may be required to read these devices” (Obviously not feasible).  Next I selected “Configure LVM” and again the existing setup was found so I just hit finished.  Now the setup screen shows all Raid and LVM mount points (ie. /boot, /usr, /swap, etc).  When I proceed to the next install step it states the “/” directory could not be found.  This is probably related to reboot message mentioned earlier.  I have tried numerous variations of this procedure which all failed in a similar manner.  In the future I might want to preserve a partition (ie. /home) on a reinstall so I must figure out this recipe.

2) Trying to redo everything from scratch.
When I get to setup partitions menu I remove everything and select create empty partitions.  Then I proceed to create the RAID/LVM exactly as I did initially.  After proceeding with the install I once again am told the “/” directory could not be found.  It is definitely one of my LVM mount points as I retried a dozen times.  *I did find that if I use different partition sizes things began to work*.  This leads to the conclusion that specifing the same structure prevents a write to the partition table.

As reinstall is essential to experimentation these problems seem vital.  I do not understand why everyone is not plagued with similar issues.  Unless my Linux Software RAID setup with LVM is not mainstream…

Thanks

---

