---
title: "Design Help: best way to swap RAID disks for fire protection"
date: 2020-01-02
forum: Hardware
---

### Post by dwsideri on 2020-01-02
I plan to design a new multipurpose Ubuntu server (DVR and NAS primarily) and am looking for a solution for protecting my data from fire/water/etc. Currently, once per month I plug in an external SSD to my server, run a script that mirrors my (old) NAS contents to the SSD, then I put the SSD in a fire-proof safe. I would like to simplify this process, if it is possible, and have a more economical way to increase the size of my fire-proof backup.

For my new server, my intention is to use an SSD for the main OS and then a two-HDD RAID-1 for the NAS. Ideally, I would like to pull one HDD from the RAID each month and replace it with "last month's" HDD from the fire-proof safe. I'm familiar with how to replace disks (failed or not) in a RAID, that's not a problem, but this is not exactly that situation.

Is there a way to streamline the disk swapping procedure? As in, perhaps, the RAID setup being smart enough to recognize that the "new" disk each month is an out-of-date member of the RAID, not an entirely new disk, so that the resilver is an update instead of a wholesale rewrite?

---

### Post by TheFu on 2020-01-02
It is your system. Do what you think will work, but a few of my thoughts.

Seems really complicated when normal backups achieve the same results without any manual steps.

Why use RAID at all?  RAID solves 2 issues - HA and perhaps improved read performance.  Trying to use it for off-line mirrors is a bastardization of the technology.  If you need HA, fine.  I can't imagine a DVR needing HA, especially in a home environment.  Use the other disk to have another slightly delayed copy of the data.

3-copies.
[LIST=1]
[*]The original files, in active use by the system
[*]Periodic backup with versioning. Every 24, 12, 6, hours - whatever you like.
[*]A mirror/rsync/clone of the versioned backups, that is off-site outside flood, earthquake, hurricane distances.
[/LIST]

For backups, use LVM+ snapshots to get a clean, quiesced, source.  ZFS snapshots can be used alternatively for this 1st-level backup.   Then use whatever backup tool you like to make the versioned backups.  It would be best if the backups are "pulled", not pushed. 

For non-media data and OSes, I have proper versioned backups.

But it is your system and an interesting idea. I doubt a sector-by-sector sync'd mirror will be anywhere as efficient as rsync.

---

