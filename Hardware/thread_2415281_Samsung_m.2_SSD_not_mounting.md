---
title: "Samsung m.2 SSD not mounting"
date: 2019-03-23
forum: Hardware
---

### Post by arcus.haios on 2019-03-23
Hello,
 I have a NVMe SSD 960 EVO M.2 250GB
It appears in GParted and in BIOS, When I try and mount it, It appears in My files, but I am unable to write to it?
It lists as /dev/nvme0n1

I eventually want to install my OS on it and format my current dual booting SSD.

---

### Post by swaraj-g7 on 2019-03-23
First, check, if your BIOS has AHCI enabled.
Option IDE is slow and my computer does not recognize this a new  Memory. This is fundamental. Then use Gparted from Ubuntu live. You should see the /nvme0n1 drive. If  yes, you can begin with installation. It should be as usual. If not,  try to create partitions using Gparted in Live Ubuntu and try it again.  Partition table should be GPT or MSDOS type. If UEFI not functioning or  you prefere reliable way , than use MSDOS.  Generally, GPT is used for large devices using UEFI. First partition should be in FAT32 format, size is about 500MB.
  I advice using older, but more conventional MSDOS. First partition  should be primary partition based on Linux File System (e.q. ext4) with  size about 1GB mapped on /boot.
For exaple, I decided to split partitions into 3 plus SWAP partiton (you  can use Swap File for now, but I don't see advantage). Tested on Ubuntu  18.04 - the both manners - UEFI and MSDOS. You can see below, what I  finally choose.
guess that might help

---

### Post by arcus.haios on 2019-03-23
I fixed it, I guess I wasn't reading M.2 In BIOS . Thanks for responding.

---

### Post by rbmorse on 2019-03-23
Withdrawn

---

