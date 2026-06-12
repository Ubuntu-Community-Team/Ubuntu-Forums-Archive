---
title: "[SOLVED] External Hard Drive(USB) Showing up as 2 hard drives"
date: 2008-04-23
forum: Hardware
---

### Post by DantePasquale on 2008-04-23
Hi Everyone,

I am running Ubuntu 7.10 64-bit and have a general external USB hard drive question. This particular hard drive was inside of my old laptop and I put a USB "wrapper" around it. Everything works fine, except that this single hard drive shows up as 2 hard drives. I think this is because I had a / and a /home filesystems on it (along with swap) and the USB drivers are picking up the 2 file systems, which was really cool when I had to recover my old laptop files.

But now, I want to use it for backups and want a single "big" volume and don't know how to get it back to one drive.

Here's some info:

**fdisk -l output**:

```

Disk /dev/sdc: 60.0 GB, 60011642368 bytes
64 heads, 32 sectors/track, 57231 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Disk identifier: 0x03ebd085

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       57231    58604528   83  Linux
```

**mount output**:

```
/dev/sdc1 on /media/disk type ext3 (rw,nosuid,nodev)
/dev/sda3 on /media/disk-1 type ext3 (rw,nosuid,nodev)
```

**df -h otuput**:

```
/dev/sdc1              56G   16G   37G  30% /media/disk
/dev/sda3              97G   62G   30G  68% /media/disk-1
```

---

### Post by jakev383 on 2008-04-23
Use gparted and modify the partitions as you see fit. You can shrink/grow them, delete, create, etc.
Should be in Synaptic and you'll need to sudo to run it.

---

