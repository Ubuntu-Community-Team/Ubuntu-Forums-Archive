---
title: "Unresponsive storage ssd"
date: 2024-03-24
forum: Hardware
---

### Post by canvas0 on 2024-03-24
I have a **ssd** with very important data in my workstation.

It has **a ext4 and a ntfs partition**.

This morning, the ext4 partition (sda1) **didn't mount, and the filesystem was listed as "unknown"** in the Disks application. running `file -s/dev/sda1` returns "**no read permissions**"; Overall assessment is marked as "Disk is OK, one bad sector", but attempting to perform any **smart self-test returns the error "sk_disk_open: input/output error (udisks-error-quark, 0)"**.

Now the ntfs partition is also listed as unknown.

Please help. I don't know what to do!

----

Additional info:

The disk is a **Samsung 870 Evo**.

It has important files and a Windows virtual machine that has been glitchy lately.

There was also a power failure recently. Not sure if it's related.

System specs:

```

System:
  Kernel: 6.5.0-21-generic x86_64 bits: 64 compiler: N/A
    Desktop: Cinnamon 5.2.7 tk: GTK 3.24.33 vt: 2 dm: GDM3 42.0
    Distro: Ubuntu 22.04.4 LTS (Jammy Jellyfish)
Machine:
  Type: Desktop System: MSI product: MS-7885 v: 1.0
    serial: <superuser required>
  Mobo: MSI model: X99A SLI PLUS(MS-7885) v: 1.0
    serial: <superuser required> UEFI-[Legacy]: American Megatrends v: 1.E0
    date: 06/15/2018
Drives:
  Local Storage: total: 3.18 TiB used: 1.63 TiB (51.1%)
  ID-1: /dev/nvme0n1 vendor: Samsung model: SSD 980 PRO 1TB
    size: 931.51 GiB speed: 63.2 Gb/s lanes: 4 type: SSD serial: <filter>
    rev: 3B2QGXA7 temp: 42.9 C scheme: MBR
  ID-2: /dev/sdb vendor: Western Digital model: WD2003FZEX-00SRLA0
    size: 1.82 TiB speed: 6.0 Gb/s type: HDD rpm: 7200 serial: <filter>
    rev: 1A01 scheme: GPT
  ID-3: /dev/sdc vendor: Samsung model: SSD 860 EVO 500GB size: 465.76 GiB
    speed: 6.0 Gb/s type: SSD serial: <filter> rev: 4B6Q scheme: MBR
Partition:
  ID-1: / size: 301.86 GiB used: 137.26 GiB (45.5%) fs: ext4 dev: /dev/sdc2
  ID-2: /mnt/hdd size: 1.82 TiB used: 1.2 TiB (66.2%) fs: ntfs
    dev: /dev/sdb2
  ID-3: /mnt/mint size: 795.67 GiB used: 295.74 GiB (37.2%) fs: ext4
    dev: /dev/nvme0n1p2
  ID-4: /mnt/nas size: 10.46 TiB used: 7.31 TiB (69.9%) fs: cifs
    dev: /dev/Aether
Swap:
  ID-1: swap-1 type: partition size: 30.52 GiB used: 0 KiB (0.0%)
    priority: -2 dev: /dev/sdc3

```

---

### Post by MAFoElffen on 2024-03-24
I would unmount the concerned partitions and do fsck on them.

---

### Post by canvas0 on 2024-03-24
> **MAFoElffen said:**
> I would unmount the concerned partitions and do fsck on them.

```
fsck from util-linux 2.37.2
e2fsck 1.46.5 (30-Dec-2021)
fsck.ext2: Input/output error while trying to open /dev/sda1

The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>

```

---

### Post by Autodave on 2024-03-25
Backups, backups, backups.  You should never have only one drive with important info on it!  Not only do I have at least 2 backups of everything in my home, I also have a complete backup HDD laying at my mom's home, disconnected from any PC, with all my stuff on it.  Every few months, I retrieve it and update it and move it back to mom's the same day.

Losing one block on a HD isn't all that bad.....unless it is the superblock.  That is bad and not normally recoverable.

---

