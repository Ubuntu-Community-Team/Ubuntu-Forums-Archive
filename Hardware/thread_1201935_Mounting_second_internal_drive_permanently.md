---
title: "Mounting second internal drive permanently"
date: 2009-07-01
forum: Hardware
---

### Post by Jeconti on 2009-07-01
I'm running Mythbuntu Jaunty. I have my second internal drive partitioned so that 30 gigs is set aside for recordings only. The trouble is that the partition never mounts automatically when the computer starts.

I tried editing my fstab to be the following: ```
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=f358c2bb-bab6-4312-afe2-2a2b8ef24d4d /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=3ebe634d-95fe-4514-9622-f9ce5f23152e none            swap    sw              0       0
#MythTV Recordings
UUID=684b1e2b-7a88-48d4-af8b-ab1b1c434df4 /media/Recordings ext4 rw
```

I copied the UUID directly from the volume information when I right click the manually mounted drive. When I enter this then restart, nothing happens. The computer still sees the drive, but attempts to mount result in failure.

---

