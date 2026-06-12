---
title: "RAID 1 recognition"
date: 2009-01-24
forum: Installation &amp; Upgrades
---

### Post by HiVoltRock on 2009-01-24
I'm trying to set up fakeRAID under Ubuntu Intrepid 64-bit. It's an nvidia controller. I tried working with dmraid to configure everything. It recognizes the array and says it's active but nothing mounts. I would like to use fakeRAID becuase I have a dual-boot with Windows and I would like BOTH operating systems to be able to read and write to the array.

I'm NOT trying to install Ubuntu on the array. I already have Ubuntu installed on a separate disk, but would like to use the array as dedicated storage in RAID 1. Is there a way to do this? I have some dmraid output if it's helpful

```
cory@cory-ubuntu:~$ sudo dmraid -r
/dev/sdd: nvidia, "nvidia_iddcebbe", mirror, ok, 1953525166 sectors, data@ 0
/dev/sdc: nvidia, "nvidia_iddcebbe", mirror, ok, 1953525166 sectors, data@ 0
cory@cory-ubuntu:~$ sudo dmraid -s
*** Active Set
name   : nvidia_iddcebbe
size   : 1953525120
stride : 128
type   : mirror
status : ok
subsets: 0
devs   : 2
spares : 0

cory@cory-ubuntu:~$ sudo dmraid -ay -v
RAID set "nvidia_iddcebbe" already active
INFO: Activating mirror RAID set "nvidia_iddcebbe"
RAID set "nvidia_iddcebbe1" already active
INFO: Activating partition RAID set "nvidia_iddcebbe1"
```

If I try to mount with gnome is says "Unable to mount volume." and "fuse: mount failed: device or resource busy"

Does anybody have any suggestions? I would really appreciate your help

---

### Post by HiVoltRock on 2009-01-28
[bump]

---

### Post by HiVoltRock on 2009-03-01
Nobody has any suggestions?

---

