---
title: "Nvidia RAID1--seems to favor only one drive.  Is this normal?"
date: 2011-06-25
forum: Hardware
---

### Post by RayChangTW on 2011-06-25
I have a fairly fresh installation of Ubuntu 11.04 on a 2 x 1tb drive  array, mirrored.  The computer seems to boot from only one drive (only  one drive light stays on or flashes at boot time).  While Transmission  is downloading a file, that same drive light will flicker often and the  other one only flashes once in a while.

**Is this normal?**

I  always imagined a RAID system to read/write at the same time.  Both  drive lights flashed in harmony during installation of Ubuntu.  Now, it  seems that there have become "primary" and "secondary" drives.  I've  researched and some people say this is called "fakeRAID".  I don't care  if it is "fake" or not, or software/hardware RAID.  I only want to know  that I have a backup.  /etc/fstab looks like one whole drive is swap  space, maybe.

I hope someone with RAID experience can comment on this.

DETAILS:
board = Gigabyte GA-M62M-S2P (about half a year old)
drives = Western Digital, about two weeks old
RAID setup = created a mirror setup with the Nvidia RAID BIOS utility (Ubuntu saw it as one drive).
system = Ubuntu 11.04
At boot-time, the Nvidia part says the RAID is "Healthy".
Example Terminal session:
```
me@me-M68M-S2P:~$ sudo dmraid -r
[sudo] password for me: 
/dev/sdb: nvidia, "nvidia_bbeggidc", mirror, ok, 1953525166 sectors, data@ 0
/dev/sda: nvidia, "nvidia_bbeggidc", mirror, ok, 1953525166 sectors, data@ 0
me@me-M68M-S2P:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/nvidia_bbeggidc1 /               ext4    errors=remount-ro 0       1
/dev/mapper/nvidia_bbeggidc5 none            swap    sw              0       0
me@me-M68M-S2P:~$ 
```

---

