---
title: "mdadm RAID1 a drive went offline"
date: 2013-09-15
forum: Hardware
---

### Post by electricman2 on 2013-09-15
I installed mdadm a few days ago and set my system up so that two identical drives mirror each other.  I was just wondering what are some options for recovery if one of those drives fail.  It should be possible to recover all data easily without replacing the drive, but every forum I've looked at just tells how to replace the drive.

Sorry, I'm a bit new to this and just started using ubuntu three days ago.

---

### Post by SaturnusDJ on 2013-09-16
There are two options besides replacing the disk.

1. You can run the array degraded. This is what happens when a member fails when the system is up and running. When this happens at downtime, you get a question at boot most times asking if you want to boot degraded.

2. A few months ago I found out that a mdadm RAID1 member is mountable exactly like a normal non-RAID disk. For example if you have an ext4 filesystem at the array, the member can be mounted as ext4. I've never had problems with this, but by bypassing the RAID layer, the mdadm superblock isn't updated. I don't know the consequences of this, it might have no impact at all.

---

### Post by electricman2 on 2013-09-22
Ok. Thanks!

---

