---
title: "XFS Bad Magic Number"
date: 2008-07-14
forum: General Help
---

### Post by cypr3ss on 2008-07-14
Hi,

Really hoping someone can help, I lost power to my main machine and now the XFS volume/partition won't mount.  I get:

[INDENT]XFS: bad magic number
XFS: SB validate failed[/INDENT]

in the output of dmesg. 

The output of xfs_check is:

[INDENT]xfs_check /dev/sdc
xfs_check: unexpected XFS SB magic number 0x33c08ed0
xfs_check: size check failed
xfs_check: read failed: Invalid argument
xfs_check: data size check failed
xfs_check: failed to alloc -225176656 bytes: Cannot allocate memory[/INDENT]

And when I try xfs_repair I get: 

[INDENT]xfs_repair -n /dev/sdc
Phase 1 - find and verify superblock...
bad primary superblock - bad magic number !!!

attempting to find secondary superblock...

...found candidate secondary superblock... unable to verify superblock, continuing...
(the above appears a few times, until finally)
...Sorry, could not find valid secondary superblock
Exiting now.[/INDENT]

Is there any chance of recovering the data?  /dev/sdc is seen by xubuntu as one ~2.2TB disk, and I put the XFS file system straight onto the disk.  It's 4x750GB drives on a hw raid controller (rocketraid 2320).  Driver for rocket raid is loaded ok, and afaict there's *something* on the disk... any chance of recovering it?  When I initially configured the file system it was running on 64bit xubuntu, now it's 32bit xubuntu, will this be a problem?

Any help greatly appreciated.

Thanks,

Cypr3ss.

---

### Post by triin mack on 2008-11-29
Yeah its 100% raid 0 fault. I also face this type of ubuntu errors and mostly errors are because of this raid problem.

---

