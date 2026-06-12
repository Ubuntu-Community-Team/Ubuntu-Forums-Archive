---
title: "Hard drive detected only sometimes"
date: 2009-10-30
forum: Hardware
---

### Post by ferchon03 on 2009-10-30
I'm having this issue since I've installed karmic final (amd64). During installation, using the desktop install CD, one of my hard drives was being detected just sometimes, let's say 1 out of 5 tries. I proceed with the installation once it was detected but now I'm having the same behavior in the new installed karmic. Let me say this never happened before, my 9.04 installation was just fine and I've tried the jaunty livecd to see what happens and it show both my HDs every time.
Something odd I've noticed is that when I start in recovery mode I can see both HDs always.
The problematic hard drive is the sdb, when it is not detected Palimpsest Disk Utility can't see it, neither Gparted. Also this HD has bad sectors, but I isolate the damage area and its not even formated (see the gap between the end of sdb2 ant the start of sdb3). Never have a problem since I've done this. Also every time I boot from it works fine.

sdb1 has W7
sdb2 has XP
sdb3 is storage (NTFS)
sdb4 is storage (EXT4)

Some info, this is the fdisk -l (when both are detected):

```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d8384

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1310    10522543+  83  Linux
/dev/sda2           38537       38913     3028252+   f  W95 Ext'd (LBA)
/dev/sda3            1311       11585    82533937+  83  Linux
/dev/sda4           11586       38536   216483907+  83  Linux
/dev/sda5           38537       38913     3028221   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6cd26f78

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        5100    40965718+   7  HPFS/NTFS
/dev/sdb2            5101        9817    37889302+   7  HPFS/NTFS
/dev/sdb3           13642       25294    93602722+   7  HPFS/NTFS
/dev/sdb4           25295       30515    41937682+  83  Linux

Disk /dev/sdc: 8027 MB, 8027897856 bytes
255 heads, 63 sectors/track, 976 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ebec1
```

blkid (when both are detected):
```
/dev/sda1: UUID="0fc4aa47-5b85-473f-8d9e-006844274578" TYPE="ext4" 
/dev/sda3: UUID="6b4a64f2-0f3f-4a10-885c-bdde0b04c453" TYPE="ext4" 
/dev/sda4: LABEL="G" UUID="24c61207-6fa5-4636-b981-cf3c927c6430" TYPE="ext4" 
/dev/sda5: UUID="ec6a6239-7566-45c0-a8b4-db979540c03e" TYPE="swap" 
/dev/sdb1: UUID="2A20BC6320BC3821" LABEL="C" TYPE="ntfs" 
/dev/sdb2: UUID="2EFCF15BFCF11DB1" LABEL="D" TYPE="ntfs" 
/dev/sdb3: UUID="15A639ACC3FC5759" LABEL="E" TYPE="ntfs" 
/dev/sdb4: LABEL="F" UUID="693dc2f9-0c38-42aa-a947-aa56650b4357" TYPE="ext4" 
```

Also the Grub2 menu has both the windows installed in sdb and works just fine.

I'll like to stay with Karmic but if I can't have both HDs I'll be forced to go back to Jaunty.
Any help will be appreciate.

---

### Post by ferchon03 on 2009-10-30
Back to Jaunty. After installing wicd I lost my wireless conection, too much to worry when Jaunty is working fine.

---

