---
title: "Disk broken? 100% READ"
date: 2013-12-21
forum: Hardware
---

### Post by jens7 on 2013-12-21
Please see the attached screenshot.
Im rebuilding /dev/sde on a 6-disk RAID 6.

/dev/sdg is stuck at 100% READ, ALL THE TIME - is the disk broken or about to die?

---

### Post by jens7 on 2013-12-23
FYI i've been recommended to take the disk out of the RAID and do some performance testing directly on the disk, if this turns out fine i'm gonna try to add it to the RAID again.

---

### Post by jens7 on 2013-12-24
Ive taken the disk out of the raid, and benchmarked read/write performance with simple dd commands.
90+ MB/s write
110+ MB/s read

No issues on the disk itself.
I've added it to the RAID again, but now sdf is acting up at 100% read.

Im gonna try and take sdf out of the RAID aswell, these are the only 2 disks originally in the RAID - Maybe Ubuntu made a mistake when creating the RAID during installation.

If anyone is experiencing similiar issues please let me know if you've found a solution.

---

