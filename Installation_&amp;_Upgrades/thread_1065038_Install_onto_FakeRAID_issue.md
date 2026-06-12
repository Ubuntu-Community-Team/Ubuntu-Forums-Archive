---
title: "Install onto FakeRAID issue"
date: 2009-02-09
forum: Installation &amp; Upgrades
---

### Post by aradapilot on 2009-02-09
I have a 4-disk SATA RAID 10 (asus controller on motherboard) set up in dmraid, and I would like to install my OS on it.  I have followed the guide at [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto) however I have encountered a problem:
dmraid displays the raid as two subsets (striped) and a superset (mirroring the striped pairs), as it should.  All sets can be activated with 'dmraid -ay', and show up in /dev/mapper.  I am able, in fdisk and parted/gparted, to see the superset and I have partitioned it appropriately (the changes are reflected on the mirrored subsets, as they should), however, when I load up the ubuntu installer and get to the partition setup (going under manual, the guided option only sees the 4 drives standalone), the 'partman' app running under this will not see the superset.  It will allow me to install on either of the subsets, but then the mirroring does not take place and it puts the raid out of sync.  It uses a Promise controller, so the devices in /dev/mapper are named as:
pdc_xxxxxx (superset, mirrors the subsets)
pdc_xxxxxx1 (partition 1)
pdc_xxxxxx-0 (striped subset 1)
pdc_xxxxxx-01 (subset 1 partition 1)
pdc_xxxxxx-1 (striped subset 2)
pdc_xxxxxx-11 (subset 2 partition 1)
and so forth.  Why does the partman segment of the ubiquity installer only see the -0 and -1 sub sets (it does see the partitions on them as well) but not the real superset enclosing them?  dmraid says it is activated successfully.
I am using an 8.10 installer (with dmraid rc14) from a flash drive, as i do not have a bootable cdrom drive on this system (asus bios bug with raid), and the dmraid rc15 available in jaunty has issues with raid10 support.
Thank you

---

### Post by avtolle on 2009-02-09
You really shouldn't post multiple threads on the same topic. Perhaps one of the mods will combine the two.

EDIT: [http://ubuntuforums.org/showthread.php?t=1065034](http://ubuntuforums.org/showthread.php?t=1065034) is your other thread, and it looks like no answers there yet, also. Did you get "bitten" by the forums going down as you were posting your first one?

---

### Post by aradapilot on 2009-02-09
woops, sorry, yes I did.

---

