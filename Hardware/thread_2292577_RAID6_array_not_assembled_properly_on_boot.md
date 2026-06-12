---
title: "RAID6 array not assembled properly on boot"
date: 2015-08-29
forum: Hardware
---

### Post by fackamato on 2015-08-29
Hi,

I've a RAID6 array that doesn't get assembled properly on on boot. If I stop the two mis-assembled arrays then just do "mdadm --assemble --scan", both the RAID6 array and the RAID0 array get assembled properly and I can then mount the partitions. Here are the details:

/etc/mdadm/mdadm.conf < all commented out. It used to have the outputs of mdadm --examine --scan in it (yes, I recreated the initramfs and rebooted to try), but the result didn't change.

Here is mdadm --examine --scan

```
ARRAY /dev/md/md0  metadata=1.2 UUID=0ad2603e:e43283ee:02180773:98e716ef name=ion:md0
ARRAY /dev/md/0  metadata=1.2 UUID=4cae433f:a40afcf5:f9aba91d:d8217b69 name=ion:0
ARRAY /dev/md/1  metadata=1.2 UUID=a20b70d4:7ee17e3f:abab74f8:dadb8cd8 name=ion:1

```

Here is cat /proc/mdstat from when it's working fine:

```
Personalities : [raid0] [raid6] [raid5] [raid4] 
md1 : active raid0 sdc2[0] sde2[2] sdd2[1]
      4098048 blocks super 1.2 512k chunks
      
md127 : active raid6 sdd1[2] sdc1[1] sdb1[0] sda1[4] sde1[3]
      5856046080 blocks super 1.2 level 6, 512k chunk, algorithm 2 [5/5] [UUUUU]
      bitmap: 0/15 pages [0KB], 65536KB chunk

unused devices: <none>

```

Here is lsblk:

```
NAME                    MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINT
sda                       8:0    0   1.8T  0 disk  
&#9492;&#9472;sda1                    8:1    0   1.8T  0 part  
  &#9492;&#9472;md127                 9:127  0   5.5T  0 raid6 /media/6TB
sdb                       8:16   0   1.8T  0 disk  
&#9492;&#9472;sdb1                    8:17   0   1.8T  0 part  
  &#9492;&#9472;md127                 9:127  0   5.5T  0 raid6 /media/6TB
sdc                       8:32   0   1.8T  0 disk  
&#9500;&#9472;sdc1                    8:33   0   1.8T  0 part  
&#9474; &#9492;&#9472;md127                 9:127  0   5.5T  0 raid6 /media/6TB
&#9492;&#9472;sdc2                    8:34   0   1.3G  0 part  
  &#9492;&#9472;md1                   9:1    0   3.9G  0 raid0 /media/4GB
sdd                       8:48   0   1.8T  0 disk  
&#9500;&#9472;sdd1                    8:49   0   1.8T  0 part  
&#9474; &#9492;&#9472;md127                 9:127  0   5.5T  0 raid6 /media/6TB
&#9492;&#9472;sdd2                    8:50   0   1.3G  0 part  
  &#9492;&#9472;md1                   9:1    0   3.9G  0 raid0 /media/4GB
sde                       8:64   0   2.7T  0 disk  
&#9500;&#9472;sde1                    8:65   0   1.8T  0 part  
&#9474; &#9492;&#9472;md127                 9:127  0   5.5T  0 raid6 /media/6TB
&#9500;&#9472;sde2                    8:66   0   1.3G  0 part  
&#9474; &#9492;&#9472;md1                   9:1    0   3.9G  0 raid0 /media/4GB
&#9492;&#9472;sde3                    8:67   0   185G  0 part  /media/198GB
sdf                       8:80   0  55.9G  0 disk  
&#9500;&#9472;sdf1                    8:81   0   243M  0 part  /boot
&#9500;&#9472;sdf2                    8:82   0     1K  0 part  
&#9492;&#9472;sdf5                    8:85   0  55.7G  0 part  
  &#9500;&#9472;ion-root (dm-0)     252:0    0  52.4G  0 lvm   /
  &#9492;&#9472;ion-swap_1 (dm-1)   252:1    0   3.3G  0 lvm   
    &#9492;&#9472;cryptswap1 (dm-2) 252:2    0   3.3G  0 crypt [SWAP]

```

[lsdrv]("https://raw.githubusercontent.com/pturmel/lsdrv/master/lsdrv"):

```
PCI [sata_mv] 06:00.0 SCSI storage controller: HighPoint Technologies, Inc. RocketRAID 230x 4 Port SATA-II Controller (rev 02)
&#9500;scsi 0:x:x:x [Empty]
&#9500;scsi 2:x:x:x [Empty]
&#9500;scsi 3:x:x:x [Empty]
&#9492;scsi 6:x:x:x [Empty]
PCI [megaraid_sas] 02:0e.0 RAID bus controller: LSI Logic / Symbios Logic MegaRAID SAS 1068
&#9500;scsi 1:2:0:0 LSI      MegaRAID 84016E  {00ede206d4a731011c50ff5e02b00506}
&#9474;&#9492;sda 1.82t [8:0] MD raid6 (6) inactive 'ion:md0' {0ad2603e-e432-83ee-0218-077398e716ef}
&#9474; &#9492;sda1 1.82t [8:1] MD raid6 (4/5) (w/ sdb1,sdc1,sdd1,sde1) in_sync 'ion:0' {4cae433f-a40a-fcf5-f9ab-a91dd8217b69}
&#9474;  &#9492;md127 5.45t [9:127] MD v1.2 raid6 (5) clean, 512k Chunk {4cae433f:a40afcf5:f9aba91d:d8217b69}
&#9474;   &#9474;                   ext4 '6TB_RAID6' {9e3c1fbe-8228-4b38-9047-66a5e2429e5f}
&#9474;   &#9492;Mounted as /dev/md127 @ /media/6TB
&#9492;scsi 1:2:1:0 LSI      MegaRAID 84016E  {0036936cc4270000ff50ff5e02b00506}
 &#9492;sdb 1.82t [8:16] MD raid6 (6) inactive 'ion:md0' {0ad2603e-e432-83ee-0218-077398e716ef}
  &#9492;sdb1 1.82t [8:17] MD raid6 (0/5) (w/ sda1,sdc1,sdd1,sde1) in_sync 'ion:0' {4cae433f-a40a-fcf5-f9ab-a91dd8217b69}
   &#9492;md127 5.45t [9:127] MD v1.2 raid6 (5) clean, 512k Chunk {4cae433f:a40afcf5:f9aba91d:d8217b69}
                        ext4 '6TB_RAID6' {9e3c1fbe-8228-4b38-9047-66a5e2429e5f}
PCI [ahci] 00:1f.2 SATA controller: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] (rev 05)
&#9500;scsi 4:0:0:0 ATA      Corsair CSSD-F60 {10326505580009990027}
&#9474;&#9492;sdf 55.90g [8:80] Partitioned (dos)
&#9474; &#9500;sdf1 243.00m [8:81] ext2 {b45c13c8-4246-43ee-ac2c-f9bb5de099f8}
&#9474; &#9474;&#9492;Mounted as /dev/sdf1 @ /boot
&#9474; &#9500;sdf2 1.00k [8:82] Partitioned (dos)
&#9474; &#9492;sdf5 55.66g [8:85] PV LVM2_member 55.66g used, 0 free {zZ5Dgy-E7v8-Y1Mi-EuqG-uXUb-DseW-s7goxG}
&#9474;  &#9492;VG ion 55.66g 0 free {XSaCyP-phLN-m4IH-2cJ7-1XXw-b3uh-qWBl8N}
&#9474;   &#9500;dm-0 52.41g [252:0] LV root ext4 {63342e0d-1b4f-4475-9835-d3a2a6610e8f}
&#9474;   &#9474;&#9492;Mounted as /dev/mapper/ion-root @ /
&#9474;   &#9492;dm-1 3.25g [252:1] LV swap_1 Empty/Unknown
&#9474;    &#9492;dm-2 3.25g [252:2] swap {4657f9cc-eb23-425e-8e4c-6b12f63a3f52}
&#9500;scsi 5:0:0:0 ATA      SAMSUNG HD204UI  {S2H7JR0B501861}
&#9474;&#9492;sdc 1.82t [8:32] MD raid6 (6) inactive 'ion:md0' {0ad2603e-e432-83ee-0218-077398e716ef}
&#9474; &#9500;sdc1 1.82t [8:33] MD raid6 (1/5) (w/ sda1,sdb1,sdd1,sde1) in_sync 'ion:0' {4cae433f-a40a-fcf5-f9ab-a91dd8217b69}
&#9474; &#9474;&#9492;md127 5.45t [9:127] MD v1.2 raid6 (5) clean, 512k Chunk {4cae433f:a40afcf5:f9aba91d:d8217b69}
&#9474; &#9474;                     ext4 '6TB_RAID6' {9e3c1fbe-8228-4b38-9047-66a5e2429e5f}
&#9474; &#9492;sdc2 1.30g [8:34] MD raid0 (0/3) (w/ sdd2,sde2) in_sync 'ion:1' {a20b70d4-7ee1-7e3f-abab-74f8dadb8cd8}
&#9474;  &#9492;md1 3.91g [9:1] MD v1.2 raid0 (3) clean, 512k Chunk, None (None) None {a20b70d4:7ee17e3f:abab74f8:dadb8cd8}
&#9474;   &#9474;               ext4 '4GB_RAID0' {c8327dd0-9d3f-4457-a73a-c9c7d5a0ee3f}
&#9474;   &#9492;Mounted as /dev/md1 @ /media/4GB
&#9500;scsi 7:x:x:x [Empty]
&#9500;scsi 8:x:x:x [Empty]
&#9500;scsi 9:0:0:0 ATA      WDC WD20EARS-00J {WD-WCAWZ2036074}
&#9474;&#9492;sdd 1.82t [8:48] MD raid6 (6) inactive 'ion:md0' {0ad2603e-e432-83ee-0218-077398e716ef}
&#9474; &#9500;sdd1 1.82t [8:49] MD raid6 (2/5) (w/ sda1,sdb1,sdc1,sde1) in_sync 'ion:0' {4cae433f-a40a-fcf5-f9ab-a91dd8217b69}
&#9474; &#9474;&#9492;md127 5.45t [9:127] MD v1.2 raid6 (5) clean, 512k Chunk {4cae433f:a40afcf5:f9aba91d:d8217b69}
&#9474; &#9474;                     ext4 '6TB_RAID6' {9e3c1fbe-8228-4b38-9047-66a5e2429e5f}
&#9474; &#9492;sdd2 1.30g [8:50] MD raid0 (1/3) (w/ sdc2,sde2) in_sync 'ion:1' {a20b70d4-7ee1-7e3f-abab-74f8dadb8cd8}
&#9474;  &#9492;md1 3.91g [9:1] MD v1.2 raid0 (3) clean, 512k Chunk, None (None) None {a20b70d4:7ee17e3f:abab74f8:dadb8cd8}
&#9474;                   ext4 '4GB_RAID0' {c8327dd0-9d3f-4457-a73a-c9c7d5a0ee3f}
&#9492;scsi 10:0:0:0 ATA      ST3000DM001-1CH1 {W1F2PZGH}
 &#9492;sde 2.73t [8:64] Partitioned (dos)
  &#9500;sde1 1.82t [8:65] MD raid6 (3/5) (w/ sda1,sdb1,sdc1,sdd1) in_sync 'ion:0' {4cae433f-a40a-fcf5-f9ab-a91dd8217b69}
  &#9474;&#9492;md127 5.45t [9:127] MD v1.2 raid6 (5) clean, 512k Chunk {4cae433f:a40afcf5:f9aba91d:d8217b69}
  &#9474;                     ext4 '6TB_RAID6' {9e3c1fbe-8228-4b38-9047-66a5e2429e5f}
  &#9500;sde2 1.30g [8:66] MD raid0 (2/3) (w/ sdc2,sdd2) in_sync 'ion:1' {a20b70d4-7ee1-7e3f-abab-74f8dadb8cd8}
  &#9474;&#9492;md1 3.91g [9:1] MD v1.2 raid0 (3) clean, 512k Chunk, None (None) None {a20b70d4:7ee17e3f:abab74f8:dadb8cd8}
  &#9474;                 ext4 '4GB_RAID0' {c8327dd0-9d3f-4457-a73a-c9c7d5a0ee3f}
  &#9492;sde3 184.98g [8:67] ext4 '198GB' {e4fc427a-4ec1-48dc-8d9b-bfcffe06d42f}
   &#9492;Mounted as /dev/sde3 @ /media/198GB

```

```
Linux ion 4.2.0-997-generic #201507180300 SMP Sat Jul 18 02:21:41 UTC 2015 i686 i686 i686 GNU/Linux
```

```
mdadm - v3.3.2-7-g21dc471 - 03th November 2014
```

dmesg:

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 4.2.0-997-generic (kernel@tangerine) (gcc version 4.8.4 (Ubuntu 4.8.4-2ubuntu1~14.04) ) #201507180300 SMP Sat Jul 18 02:21:41 UTC 2015
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] x86/fpu: Supporting XSAVE feature 0x01: 'x87 floating point registers'
[    0.000000] x86/fpu: Supporting XSAVE feature 0x02: 'SSE registers'
[    0.000000] x86/fpu: Enabled xstate features 0x3, context size is 0x240 bytes, using 'standard' format.
[    0.000000] x86/fpu: Using 'eager' FPU context switches.
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009cbff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009cc00-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000b98b1fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000b98b2000-0x00000000b98b8fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000b98b9000-0x00000000b9cfbfff] usable
[    0.000000] BIOS-e820: [mem 0x00000000b9cfc000-0x00000000ba28cfff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ba28d000-0x00000000ccdaffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000ccdb0000-0x00000000cce47fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000cce48000-0x00000000cce98fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000cce99000-0x00000000ccfc7fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000ccfc8000-0x00000000cdffefff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000cdfff000-0x00000000cdffffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000cf000000-0x00000000df1fffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000f8000000-0x00000000fbffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed00000-0x00000000fed03fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000011edfffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.8 present.
[    0.000000] DMI: MSI MS-7817/B85M-E33 (MS-7817), BIOS V3.7 07/17/2014
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] e820: last_pfn = 0x11ee00 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-D7FFF write-protect
[    0.000000]   D8000-E7FFF uncachable
[    0.000000]   E8000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask 7F00000000 write-back
[    0.000000]   1 base 0100000000 mask 7FE0000000 write-back
[    0.000000]   2 base 00E0000000 mask 7FE0000000 uncachable
[    0.000000]   3 base 00D0000000 mask 7FF0000000 uncachable
[    0.000000]   4 base 00CF000000 mask 7FFF000000 uncachable
[    0.000000]   5 base 011F000000 mask 7FFF000000 uncachable
[    0.000000]   6 base 011EE00000 mask 7FFFE00000 uncachable
[    0.000000]   7 disabled
[    0.000000]   8 disabled
[    0.000000]   9 disabled
[    0.000000] x86/PAT: Configuration [0-7]: WB  WC  UC- UC  WB  WC  UC- WT  
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 4GB, type WB
[    0.000000] reg 1, base: 4GB, range: 512MB, type WB
[    0.000000] reg 2, base: 3584MB, range: 512MB, type UC
[    0.000000] reg 3, base: 3328MB, range: 256MB, type UC
[    0.000000] reg 4, base: 3312MB, range: 16MB, type UC
[    0.000000] reg 5, base: 4592MB, range: 16MB, type UC
[    0.000000] reg 6, base: 4590MB, range: 2MB, type UC
[    0.000000] total RAM covered: 3806M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K 	chunk_size: 32M 	num_reg: 7  	lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3GB, range: 256MB, type WB
[    0.000000] reg 3, base: 3312MB, range: 16MB, type UC
[    0.000000] reg 4, base: 4GB, range: 512MB, type WB
[    0.000000] reg 5, base: 4590MB, range: 2MB, type UC
[    0.000000] reg 6, base: 4592MB, range: 16MB, type UC
[    0.000000] e820: update [mem 0xcf000000-0xffffffff] usable ==> reserved
[    0.000000] found SMP MP-table at [mem 0x000fd7e0-0x000fd7ef] mapped at [c00fd7e0]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] initial memory mapped: [mem 0x00000000-0x021fffff]
[    0.000000] Base memory trampoline at [c0098000] 98000 size 16384
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] init_memory_mapping: [mem 0x37800000-0x379fffff]
[    0.000000]  [mem 0x37800000-0x379fffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x20000000-0x377fffff]
[    0.000000]  [mem 0x20000000-0x377fffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0x1fffffff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x1fffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x37a00000-0x37bfdfff]
[    0.000000]  [mem 0x37a00000-0x37bfdfff] page 4k
[    0.000000] BRK [0x01c88000, 0x01c88fff] PGTABLE
[    0.000000] BRK [0x01c89000, 0x01c89fff] PGTABLE
[    0.000000] RAMDISK: [mem 0x350d4000-0x36861fff]
[    0.000000] ACPI: Early table checksum verification disabled
[    0.000000] ACPI: RSDP 0x00000000000F04A0 000024 (v02 ALASKA)
[    0.000000] ACPI: XSDT 0x00000000CCF9B080 00007C (v01 ALASKA A M I    01072009 AMI  00010013)
[    0.000000] ACPI: FACP 0x00000000CCFA8668 00010C (v05 ALASKA A M I    01072009 AMI  00010013)
[    0.000000] ACPI: DSDT 0x00000000CCF9B190 00D4D2 (v02 ALASKA A M I    00000036 INTL 20120711)
[    0.000000] ACPI: FACS 0x00000000CCFC7F80 000040
[    0.000000] ACPI: APIC 0x00000000CCFA8778 000062 (v03 ALASKA A M I    01072009 AMI  00010013)
[    0.000000] ACPI: FPDT 0x00000000CCFA87E0 000044 (v01 ALASKA A M I    01072009 AMI  00010013)
[    0.000000] ACPI: SSDT 0x00000000CCFA8828 000539 (v01 PmRef  Cpu0Ist  00003000 INTL 20120711)
[    0.000000] ACPI: SSDT 0x00000000CCFA8D68 000AD8 (v01 PmRef  CpuPm    00003000 INTL 20120711)
[    0.000000] ACPI: MCFG 0x00000000CCFA9840 00003C (v01 ALASKA A M I    01072009 MSFT 00000097)
[    0.000000] ACPI: HPET 0x00000000CCFA9880 000038 (v01 ALASKA A M I    01072009 AMI. 00000005)
[    0.000000] ACPI: SSDT 0x00000000CCFA98B8 00036D (v01 SataRe SataTabl 00001000 INTL 20120711)
[    0.000000] ACPI: SSDT 0x00000000CCFA9C28 003528 (v01 SaSsdt SaSsdt   00003000 INTL 20091112)
[    0.000000] ACPI: ASF! 0x00000000CCFAD150 0000A5 (v32 INTEL   HCG     00000001 TFSM 000F4240)
[    0.000000] ACPI: SSDT 0x00000000CCFAD1F8 000A26 (v01 Intel_ IsctTabl 00001000 INTL 20120711)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 3698MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x0000000000001000-0x0000000000ffffff]
[    0.000000]   Normal   [mem 0x0000000001000000-0x0000000037bfdfff]
[    0.000000]   HighMem  [mem 0x0000000037bfe000-0x000000011edfffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x0000000000001000-0x000000000009bfff]
[    0.000000]   node   0: [mem 0x0000000000100000-0x00000000b98b1fff]
[    0.000000]   node   0: [mem 0x00000000b98b9000-0x00000000b9cfbfff]
[    0.000000]   node   0: [mem 0x00000000ba28d000-0x00000000ccdaffff]
[    0.000000]   node   0: [mem 0x00000000cce48000-0x00000000cce98fff]
[    0.000000]   node   0: [mem 0x00000000cdfff000-0x00000000cdffffff]
[    0.000000]   node   0: [mem 0x0000000100000000-0x000000011edfffff]
[    0.000000] Initmem setup node 0 [mem 0x0000000000001000-0x000000011edfffff]
[    0.000000] On node 0 totalpages: 964101
[    0.000000]   DMA zone: 40 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3995 pages, LIFO batch:0
[    0.000000]   Normal zone: 2190 pages used for memmap
[    0.000000]   Normal zone: 224254 pages, LIFO batch:31
[    0.000000]   HighMem zone: 735852 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] Reserving Intel graphics stolen memory at 0xcf200000-0xdf1fffff
[    0.000000] ACPI: PM-Timer IO Port: 0x1808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1])
[    0.000000] IOAPIC[0]: apic_id 8, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] smpboot: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: [mem 0x00000000-0x00000fff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009c000-0x0009cfff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009d000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
[    0.000000] e820: [mem 0xdf200000-0xf7ffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] clocksource: refined-jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645519600211568 ns
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 19 pages/cpu @f6cb1000 s46732 r0 d31092 u77824
[    0.000000] pcpu-alloc: s46732 r0 d31092 u77824 alloc=19*4096
[    0.000000] pcpu-alloc: [0] 0 [0] 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 961871
[    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-4.2.0-997-generic root=/dev/mapper/ion-root ro fastboot elevator=deadline irqpoll
[    0.000000] Misrouted IRQ fixup and polling support enabled
[    0.000000] This may significantly impact system performance
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] Initializing HighMem for node 0 (00037bfe:0011ee00)
[    0.000000] Initializing Movable for node 0 (00000000:00000000)
[    0.000000] Memory: 3777304K/3856404K available (7163K kernel code, 735K rwdata, 3064K rodata, 964K init, 792K bss, 79100K reserved, 0K cma-reserved, 2943408K highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff15000 - 0xfffff000   ( 936 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
[    0.000000]       .init : 0xc1ab8000 - 0xc1ba9000   ( 964 kB)
[    0.000000]       .data : 0xc16ff295 - 0xc1ab6e80   (3806 kB)
[    0.000000]       .text : 0xc1000000 - 0xc16ff295   (7164 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	Build-time adjustment of leaf fanout to 32.
[    0.000000] 	RCU restricting CPUs from NR_CPUS=8 to nr_cpu_ids=2.
[    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=32, nr_cpu_ids=2
[    0.000000] NR_IRQS:2304 nr_irqs:440 16
[    0.000000] CPU 0 irqstacks, hard=f3036000 soft=f3038000
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] clocksource: hpet: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 133484882848 ns
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] tsc: Detected 3200.046 MHz processor
[    0.000021] Calibrating delay loop (skipped), value calculated using timer frequency.. 6400.09 BogoMIPS (lpj=12800184)
[    0.000090] pid_max: default: 32768 minimum: 301
[    0.000125] ACPI: Core revision 20150619
[    0.008117] ACPI: All ACPI Tables successfully acquired
[    0.008185] Security Framework initialized
[    0.008220] AppArmor: AppArmor initialized
[    0.008252] Yama: becoming mindful.
[    0.008303] Mount-cache hash table entries: 2048 (order: 1, 8192 bytes)
[    0.008340] Mountpoint-cache hash table entries: 2048 (order: 1, 8192 bytes)
[    0.008487] Initializing cgroup subsys blkio
[    0.008520] Initializing cgroup subsys memory
[    0.008555] Initializing cgroup subsys devices
[    0.008589] Initializing cgroup subsys freezer
[    0.008621] Initializing cgroup subsys net_cls
[    0.008654] Initializing cgroup subsys perf_event
[    0.008687] Initializing cgroup subsys net_prio
[    0.008721] Initializing cgroup subsys hugetlb
[    0.008768] CPU: Physical Processor ID: 0
[    0.008800] CPU: Processor Core ID: 0
[    0.010352] mce: CPU supports 7 MCE banks
[    0.010391] CPU0: Thermal monitoring enabled (TM1)
[    0.010429] process: using mwait in idle threads
[    0.010484] Last level iTLB entries: 4KB 1024, 2MB 1024, 4MB 1024
[    0.010519] Last level dTLB entries: 4KB 1024, 2MB 1024, 4MB 1024, 1GB 4
[    0.010924] Freeing SMP alternatives memory: 28K (c1ba9000 - c1bb0000)
[    0.021365] ftrace: allocating 30040 entries in 59 pages
[    0.029859] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.030220] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=0 pin2=0
[    0.069941] TSC deadline timer enabled
[    0.069943] smpboot: CPU0: Intel(R) Pentium(R) CPU G3420 @ 3.20GHz (fam: 06, model: 3c, stepping: 03)
[    0.070053] Performance Events: PEBS fmt2+, 16-deep LBR, Haswell events, full-width counters, Intel PMU driver.
[    0.070184] ... version:                3
[    0.070216] ... bit width:              48
[    0.070248] ... generic registers:      8
[    0.070279] ... value mask:             0000ffffffffffff
[    0.070312] ... max period:             0000ffffffffffff
[    0.070346] ... fixed-purpose events:   3
[    0.071097] ... event mask:             00000007000000ff
[    0.071692] CPU 1 irqstacks, hard=f317c000 soft=f317e000
[    0.071693] x86: Booting SMP configuration:
[    0.071725] .... node  #0, CPUs:      #1
[    0.072868] Initializing CPU#1
[    0.076479] x86: Booted up 1 node, 2 CPUs
[    0.076567] smpboot: Total of 2 processors activated (12800.18 BogoMIPS)
[    0.076626] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.077948] devtmpfs: initialized
[    0.078188] evm: security.selinux
[    0.078219] evm: security.SMACK64
[    0.078248] evm: security.SMACK64EXEC
[    0.078279] evm: security.SMACK64TRANSMUTE
[    0.078311] evm: security.SMACK64MMAP
[    0.078342] evm: security.ima
[    0.078372] evm: security.capability
[    0.078467] PM: Registering ACPI NVS region [mem 0xb98b2000-0xb98b8fff] (28672 bytes)
[    0.078516] PM: Registering ACPI NVS region [mem 0xcce99000-0xccfc7fff] (1241088 bytes)
[    0.078621] clocksource: jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645041785100000 ns
[    0.078722] pinctrl core: initialized pinctrl subsystem
[    0.078833] RTC time: 12:34:43, date: 08/29/15
[    0.078948] NET: Registered protocol family 16
[    0.079107] EISA bus registered
[    0.088507] cpuidle: using governor ladder
[    0.100517] cpuidle: using governor menu
[    0.100631] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.100681] ACPI: bus type PCI registered
[    0.100713] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.100792] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.100845] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
[    0.100881] PCI: Using MMCONFIG for extended config space
[    0.100915] PCI: Using configuration type 1 for base access
[    0.101058] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.101115] perf_event_intel: PMU erratum BJ122, BV98, HSD29 workaround disabled, HT off
[    0.110219] ACPI: Added _OSI(Module Device)
[    0.110252] ACPI: Added _OSI(Processor Device)
[    0.110285] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.110318] ACPI: Added _OSI(Processor Aggregator Device)
[    0.112898] ACPI: Executed 1 blocks of module-level executable AML code
[    0.114684] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.115172] ACPI: Dynamic OEM Table Load:
[    0.115233] ACPI: SSDT 0x00000000F31EE400 0003D3 (v01 PmRef  Cpu0Cst  00003001 INTL 20120711)
[    0.115749] ACPI: Dynamic OEM Table Load:
[    0.115809] ACPI: SSDT 0x00000000F3012000 0005AA (v01 PmRef  ApIst    00003000 INTL 20120711)
[    0.116344] ACPI: Dynamic OEM Table Load:
[    0.116402] ACPI: SSDT 0x00000000F31B6600 000119 (v01 PmRef  ApCst    00003000 INTL 20120711)
[    0.116942] ACPI: Interpreter enabled
[    0.116978] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20150619/hwxface-580)
[    0.117058] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20150619/hwxface-580)
[    0.117143] ACPI: (supports S0 S3 S4 S5)
[    0.117175] ACPI: Using IOAPIC for interrupt routing
[    0.117226] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.122634] ACPI: Power Resource [FN00] (off)
[    0.122717] ACPI: Power Resource [FN01] (off)
[    0.122798] ACPI: Power Resource [FN02] (off)
[    0.122879] ACPI: Power Resource [FN03] (off)
[    0.122959] ACPI: Power Resource [FN04] (off)
[    0.123507] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3e])
[    0.123545] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.123739] acpi PNP0A08:00: _OSC: platform does not support [PCIeHotplug PME]
[    0.123864] acpi PNP0A08:00: _OSC: OS now controls [AER PCIeCapability]
[    0.123900] acpi PNP0A08:00: FADT indicates ASPM is unsupported, using BIOS configuration
[    0.124202] PCI host bridge to bus 0000:00
[    0.124235] pci_bus 0000:00: root bus resource [bus 00-3e]
[    0.124269] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7 window]
[    0.124306] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff window]
[    0.124343] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff window]
[    0.124393] pci_bus 0000:00: root bus resource [mem 0x000d8000-0x000dbfff window]
[    0.124442] pci_bus 0000:00: root bus resource [mem 0x000dc000-0x000dffff window]
[    0.124492] pci_bus 0000:00: root bus resource [mem 0x000e0000-0x000e3fff window]
[    0.124541] pci_bus 0000:00: root bus resource [mem 0x000e4000-0x000e7fff window]
[    0.124591] pci_bus 0000:00: root bus resource [mem 0xdf200000-0xfeafffff window]
[    0.124644] pci 0000:00:00.0: [8086:0c00] type 00 class 0x060000
[    0.124701] pci 0000:00:01.0: [8086:0c01] type 01 class 0x060400
[    0.124725] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.124776] pci 0000:00:01.0: System wakeup disabled by ACPI
[    0.124840] pci 0000:00:02.0: [8086:0402] type 00 class 0x030000
[    0.124850] pci 0000:00:02.0: reg 0x10: [mem 0xf7400000-0xf77fffff 64bit]
[    0.124854] pci 0000:00:02.0: reg 0x18: [mem 0xe0000000-0xefffffff 64bit pref]
[    0.124858] pci 0000:00:02.0: reg 0x20: [io  0xf000-0xf03f]
[    0.124909] pci 0000:00:03.0: [8086:0c0c] type 00 class 0x040300
[    0.124918] pci 0000:00:03.0: reg 0x10: [mem 0xf7c10000-0xf7c13fff 64bit]
[    0.124990] pci 0000:00:14.0: [8086:8c31] type 00 class 0x0c0330
[    0.125012] pci 0000:00:14.0: reg 0x10: [mem 0xf7c00000-0xf7c0ffff 64bit]
[    0.125053] pci 0000:00:14.0: PME# supported from D3hot D3cold
[    0.125077] pci 0000:00:14.0: System wakeup disabled by ACPI
[    0.125138] pci 0000:00:16.0: [8086:8c3a] type 00 class 0x078000
[    0.125161] pci 0000:00:16.0: reg 0x10: [mem 0xf7c1a000-0xf7c1a00f 64bit]
[    0.125205] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.125261] pci 0000:00:1a.0: [8086:8c2d] type 00 class 0x0c0320
[    0.125285] pci 0000:00:1a.0: reg 0x10: [mem 0xf7c18000-0xf7c183ff]
[    0.125344] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.125377] pci 0000:00:1a.0: System wakeup disabled by ACPI
[    0.125438] pci 0000:00:1c.0: [8086:8c10] type 01 class 0x060400
[    0.125489] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.125534] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    0.125595] pci 0000:00:1c.2: [8086:8c14] type 01 class 0x060400
[    0.125645] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.125687] pci 0000:00:1c.2: System wakeup disabled by ACPI
[    0.125749] pci 0000:00:1c.3: [8086:8c16] type 01 class 0x060400
[    0.125799] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.125841] pci 0000:00:1c.3: System wakeup disabled by ACPI
[    0.125907] pci 0000:00:1d.0: [8086:8c26] type 00 class 0x0c0320
[    0.125931] pci 0000:00:1d.0: reg 0x10: [mem 0xf7c17000-0xf7c173ff]
[    0.125990] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.126025] pci 0000:00:1d.0: System wakeup disabled by ACPI
[    0.126090] pci 0000:00:1f.0: [8086:8c50] type 00 class 0x060100
[    0.126219] pci 0000:00:1f.2: [8086:8c02] type 00 class 0x010601
[    0.126237] pci 0000:00:1f.2: reg 0x10: [io  0xf0b0-0xf0b7]
[    0.126243] pci 0000:00:1f.2: reg 0x14: [io  0xf0a0-0xf0a3]
[    0.126249] pci 0000:00:1f.2: reg 0x18: [io  0xf090-0xf097]
[    0.126256] pci 0000:00:1f.2: reg 0x1c: [io  0xf080-0xf083]
[    0.126262] pci 0000:00:1f.2: reg 0x20: [io  0xf060-0xf07f]
[    0.126269] pci 0000:00:1f.2: reg 0x24: [mem 0xf7c16000-0xf7c167ff]
[    0.126288] pci 0000:00:1f.2: PME# supported from D3hot
[    0.126334] pci 0000:00:1f.3: [8086:8c22] type 00 class 0x0c0500
[    0.126348] pci 0000:00:1f.3: reg 0x10: [mem 0xf7c15000-0xf7c150ff 64bit]
[    0.126365] pci 0000:00:1f.3: reg 0x20: [io  0xf040-0xf05f]
[    0.126447] pci 0000:01:00.0: [8086:0370] type 01 class 0x060400
[    0.126486] pci 0000:01:00.0: PME# supported from D0 D3hot D3cold
[    0.126497] pci 0000:01:00.0: System wakeup disabled by ACPI
[    0.126557] pci 0000:01:00.2: [8086:0372] type 01 class 0x060400
[    0.126596] pci 0000:01:00.2: PME# supported from D0 D3hot D3cold
[    0.134038] pci 0000:00:01.0: PCI bridge to [bus 01-03]
[    0.134074] pci 0000:00:01.0:   bridge window [mem 0xf7b00000-0xf7bfffff]
[    0.134077] pci 0000:00:01.0:   bridge window [mem 0xf0100000-0xf01fffff 64bit pref]
[    0.134119] pci 0000:02:0e.0: [1000:0411] type 00 class 0x010400
[    0.134145] pci 0000:02:0e.0: reg 0x10: [mem 0xf0100000-0xf010ffff pref]
[    0.134160] pci 0000:02:0e.0: reg 0x18: [mem 0xf7b00000-0xf7b3ffff]
[    0.134187] pci 0000:02:0e.0: reg 0x30: [mem 0xf7b40000-0xf7b47fff pref]
[    0.134207] pci 0000:02:0e.0: supports D1
[    0.134241] pci 0000:01:00.0: PCI bridge to [bus 02]
[    0.134277] pci 0000:01:00.0:   bridge window [mem 0xf7b00000-0xf7bfffff]
[    0.134280] pci 0000:01:00.0:   bridge window [mem 0xf0100000-0xf01fffff 64bit pref]
[    0.134327] pci 0000:01:00.2: PCI bridge to [bus 03]
[    0.134417] acpiphp: Slot [1] registered
[    0.134451] pci 0000:00:1c.0: PCI bridge to [bus 04]
[    0.134545] pci 0000:05:00.0: [10ec:8168] type 00 class 0x020000
[    0.134582] pci 0000:05:00.0: reg 0x10: [io  0xe000-0xe0ff]
[    0.134609] pci 0000:05:00.0: reg 0x18: [mem 0xf7a00000-0xf7a00fff 64bit]
[    0.134625] pci 0000:05:00.0: reg 0x20: [mem 0xf0000000-0xf0003fff 64bit pref]
[    0.134681] pci 0000:05:00.0: supports D1 D2
[    0.134682] pci 0000:05:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.134706] pci 0000:05:00.0: System wakeup disabled by ACPI
[    0.142063] pci 0000:00:1c.2: PCI bridge to [bus 05]
[    0.142098] pci 0000:00:1c.2:   bridge window [io  0xe000-0xefff]
[    0.142101] pci 0000:00:1c.2:   bridge window [mem 0xf7a00000-0xf7afffff]
[    0.142106] pci 0000:00:1c.2:   bridge window [mem 0xf0000000-0xf00fffff 64bit pref]
[    0.142162] pci 0000:06:00.0: [1103:2300] type 00 class 0x010000
[    0.142200] pci 0000:06:00.0: reg 0x10: [mem 0xf7800000-0xf78fffff 64bit]
[    0.142211] pci 0000:06:00.0: reg 0x18: [io  0xd000-0xd0ff]
[    0.142293] pci 0000:06:00.0: System wakeup disabled by ACPI
[    0.150080] pci 0000:00:1c.3: PCI bridge to [bus 06]
[    0.150115] pci 0000:00:1c.3:   bridge window [io  0xd000-0xdfff]
[    0.150118] pci 0000:00:1c.3:   bridge window [mem 0xf7800000-0xf79fffff]
[    0.150144] pci_bus 0000:00: on NUMA node 0
[    0.150573] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.150783] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.151030] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 *10 11 12 14 15)
[    0.151236] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 10 11 12 14 15)
[    0.151441] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.151684] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.151928] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.152175] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 6 10 11 12 14 15)
[    0.152566] ACPI: Enabled 4 GPEs in block 00 to 3F
[    0.152692] vgaarb: setting as boot device: PCI:0000:00:02.0
[    0.152727] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.152778] vgaarb: loaded
[    0.152807] vgaarb: bridge control possible 0000:00:02.0
[    0.153023] SCSI subsystem initialized
[    0.153077] libata version 3.00 loaded.
[    0.153093] ACPI: bus type USB registered
[    0.153135] usbcore: registered new interface driver usbfs
[    0.153175] usbcore: registered new interface driver hub
[    0.153214] usbcore: registered new device driver usb
[    0.153337] PCI: Using ACPI for IRQ routing
[    0.154544] PCI: pci_cache_line_size set to 64 bytes
[    0.154589] e820: reserve RAM buffer [mem 0x0009cc00-0x0009ffff]
[    0.154590] e820: reserve RAM buffer [mem 0xb98b2000-0xbbffffff]
[    0.154591] e820: reserve RAM buffer [mem 0xb9cfc000-0xbbffffff]
[    0.154592] e820: reserve RAM buffer [mem 0xccdb0000-0xcfffffff]
[    0.154593] e820: reserve RAM buffer [mem 0xcce99000-0xcfffffff]
[    0.154595] e820: reserve RAM buffer [mem 0xce000000-0xcfffffff]
[    0.154596] e820: reserve RAM buffer [mem 0x11ee00000-0x11fffffff]
[    0.154669] NetLabel: Initializing
[    0.154700] NetLabel:  domain hash size = 128
[    0.154732] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.154773] NetLabel:  unlabeled traffic allowed by default
[    0.154883] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.155035] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.157085] clocksource: Switched to clocksource hpet
[    0.161960] AppArmor: AppArmor Filesystem Enabled
[    0.162044] pnp: PnP ACPI init
[    0.162138] system 00:00: [mem 0xfed40000-0xfed44fff] has been reserved
[    0.162176] system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.162288] system 00:01: [io  0x0680-0x069f] has been reserved
[    0.162324] system 00:01: [io  0xffff] has been reserved
[    0.162357] system 00:01: [io  0xffff] has been reserved
[    0.162392] system 00:01: [io  0xffff] has been reserved
[    0.162426] system 00:01: [io  0x1c00-0x1cfe] has been reserved
[    0.162461] system 00:01: [io  0x1d00-0x1dfe] has been reserved
[    0.162497] system 00:01: [io  0x1e00-0x1efe] has been reserved
[    0.162532] system 00:01: [io  0x1f00-0x1ffe] has been reserved
[    0.162567] system 00:01: [io  0x1800-0x18fe] could not be reserved
[    0.162603] system 00:01: [io  0x164e-0x164f] has been reserved
[    0.162639] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.162656] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.162686] system 00:03: [io  0x1854-0x1857] has been reserved
[    0.162722] system 00:03: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.162786] system 00:04: [io  0x0a00-0x0a0f] has been reserved
[    0.162821] system 00:04: [io  0x0a10-0x0a1f] has been reserved
[    0.162856] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.162904] system 00:05: [io  0x04d0-0x04d1] has been reserved
[    0.162940] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.163210] system 00:06: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.163246] system 00:06: [mem 0xfed10000-0xfed17fff] has been reserved
[    0.163283] system 00:06: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.163320] system 00:06: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.163356] system 00:06: [mem 0xf8000000-0xfbffffff] has been reserved
[    0.163393] system 00:06: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.163429] system 00:06: [mem 0xfed90000-0xfed93fff] has been reserved
[    0.163466] system 00:06: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.163503] system 00:06: [mem 0xff000000-0xffffffff] has been reserved
[    0.163539] system 00:06: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.163576] system 00:06: [mem 0xf7fdf000-0xf7fdffff] has been reserved
[    0.163613] system 00:06: [mem 0xf7fe0000-0xf7feffff] has been reserved
[    0.163650] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.163783] pnp: PnP ACPI: found 7 devices
[    0.163816] PnPBIOS: Disabled by ACPI PNP
[    0.199788] clocksource: acpi_pm: mask: 0xffffff max_cycles: 0xffffff, max_idle_ns: 2085701024 ns
[    0.199862] pci 0000:00:1c.0: bridge window [io  0x1000-0x0fff] to [bus 04] add_size 1000
[    0.199864] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 04] add_size 200000 add_align 100000
[    0.199866] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff] to [bus 04] add_size 200000 add_align 100000
[    0.199879] pci 0000:00:1c.0: res[14]=[mem 0x00100000-0x000fffff] res_to_dev_res add_size 200000 min_align 100000
[    0.199880] pci 0000:00:1c.0: res[14]=[mem 0x00100000-0x002fffff] res_to_dev_res add_size 200000 min_align 100000
[    0.199882] pci 0000:00:1c.0: res[15]=[mem 0x00100000-0x000fffff 64bit pref] res_to_dev_res add_size 200000 min_align 100000
[    0.199883] pci 0000:00:1c.0: res[15]=[mem 0x00100000-0x002fffff 64bit pref] res_to_dev_res add_size 200000 min_align 100000
[    0.199884] pci 0000:00:1c.0: res[13]=[io  0x1000-0x0fff] res_to_dev_res add_size 1000 min_align 1000
[    0.199886] pci 0000:00:1c.0: res[13]=[io  0x1000-0x1fff] res_to_dev_res add_size 1000 min_align 1000
[    0.199890] pci 0000:00:1c.0: BAR 14: assigned [mem 0xdf200000-0xdf3fffff]
[    0.199931] pci 0000:00:1c.0: BAR 15: assigned [mem 0xdf400000-0xdf5fffff 64bit pref]
[    0.199982] pci 0000:00:1c.0: BAR 13: assigned [io  0x2000-0x2fff]
[    0.200018] pci 0000:01:00.0: PCI bridge to [bus 02]
[    0.200773] pci 0000:01:00.0:   bridge window [mem 0xf7b00000-0xf7bfffff]
[    0.200811] pci 0000:01:00.0:   bridge window [mem 0xf0100000-0xf01fffff 64bit pref]
[    0.200864] pci 0000:01:00.2: PCI bridge to [bus 03]
[    0.200903] pci 0000:00:01.0: PCI bridge to [bus 01-03]
[    0.200938] pci 0000:00:01.0:   bridge window [mem 0xf7b00000-0xf7bfffff]
[    0.200975] pci 0000:00:01.0:   bridge window [mem 0xf0100000-0xf01fffff 64bit pref]
[    0.201026] pci 0000:00:1c.0: PCI bridge to [bus 04]
[    0.201061] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.201103] pci 0000:00:1c.0:   bridge window [mem 0xdf200000-0xdf3fffff]
[    0.201140] pci 0000:00:1c.0:   bridge window [mem 0xdf400000-0xdf5fffff 64bit pref]
[    0.201193] pci 0000:00:1c.2: PCI bridge to [bus 05]
[    0.201227] pci 0000:00:1c.2:   bridge window [io  0xe000-0xefff]
[    0.201265] pci 0000:00:1c.2:   bridge window [mem 0xf7a00000-0xf7afffff]
[    0.201303] pci 0000:00:1c.2:   bridge window [mem 0xf0000000-0xf00fffff 64bit pref]
[    0.201356] pci 0000:00:1c.3: PCI bridge to [bus 06]
[    0.201389] pci 0000:00:1c.3:   bridge window [io  0xd000-0xdfff]
[    0.201427] pci 0000:00:1c.3:   bridge window [mem 0xf7800000-0xf79fffff]
[    0.201469] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7 window]
[    0.201470] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff window]
[    0.201471] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff window]
[    0.201473] pci_bus 0000:00: resource 7 [mem 0x000d8000-0x000dbfff window]
[    0.201474] pci_bus 0000:00: resource 8 [mem 0x000dc000-0x000dffff window]
[    0.201475] pci_bus 0000:00: resource 9 [mem 0x000e0000-0x000e3fff window]
[    0.201476] pci_bus 0000:00: resource 10 [mem 0x000e4000-0x000e7fff window]
[    0.201477] pci_bus 0000:00: resource 11 [mem 0xdf200000-0xfeafffff window]
[    0.201478] pci_bus 0000:01: resource 1 [mem 0xf7b00000-0xf7bfffff]
[    0.201479] pci_bus 0000:01: resource 2 [mem 0xf0100000-0xf01fffff 64bit pref]
[    0.201480] pci_bus 0000:02: resource 1 [mem 0xf7b00000-0xf7bfffff]
[    0.201481] pci_bus 0000:02: resource 2 [mem 0xf0100000-0xf01fffff 64bit pref]
[    0.201482] pci_bus 0000:04: resource 0 [io  0x2000-0x2fff]
[    0.201483] pci_bus 0000:04: resource 1 [mem 0xdf200000-0xdf3fffff]
[    0.201484] pci_bus 0000:04: resource 2 [mem 0xdf400000-0xdf5fffff 64bit pref]
[    0.201486] pci_bus 0000:05: resource 0 [io  0xe000-0xefff]
[    0.201487] pci_bus 0000:05: resource 1 [mem 0xf7a00000-0xf7afffff]
[    0.201488] pci_bus 0000:05: resource 2 [mem 0xf0000000-0xf00fffff 64bit pref]
[    0.201489] pci_bus 0000:06: resource 0 [io  0xd000-0xdfff]
[    0.201490] pci_bus 0000:06: resource 1 [mem 0xf7800000-0xf79fffff]
[    0.201510] NET: Registered protocol family 2
[    0.201633] TCP established hash table entries: 8192 (order: 3, 32768 bytes)
[    0.201676] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.201719] TCP: Hash tables configured (established 8192 bind 8192)
[    0.201762] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.201799] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.201855] NET: Registered protocol family 1
[    0.201897] pci 0000:00:02.0: Video device with shadowed ROM
[    0.202181] pci 0000:01:00.0: rerouting interrupts for [8086:0370]
[    0.202218] pci 0000:01:00.2: rerouting interrupts for [8086:0372]
[    0.202260] PCI: CLS 64 bytes, default 64
[    0.202294] Trying to unpack rootfs image as initramfs...
[    0.510196] Freeing initrd memory: 24120K (f50d4000 - f6862000)
[    0.511010] RAPL PMU detected, API unit is 2^-32 Joules, 4 fixed counters 655360 ms ovfl timer
[    0.511062] hw unit of domain pp0-core 2^-14 Joules
[    0.511095] hw unit of domain package 2^-14 Joules
[    0.511128] hw unit of domain dram 2^-14 Joules
[    0.511161] hw unit of domain pp1-gpu 2^-14 Joules
[    0.511262] microcode: CPU0 sig=0x306c3, pf=0x2, revision=0x19
[    0.511302] microcode: CPU1 sig=0x306c3, pf=0x2, revision=0x19
[    0.511369] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.511474] Scanning for low memory corruption every 60 seconds
[    0.511686] futex hash table entries: 512 (order: 3, 32768 bytes)
[    0.511729] Initialise system trusted keyring
[    0.511779] audit: initializing netlink subsys (disabled)
[    0.511821] audit: type=2000 audit(1440851683.504:1): initialized
[    0.512077] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.513176] zpool: loaded
[    0.513207] zbud: loaded
[    0.513286] VFS: Disk quotas dquot_6.6.0
[    0.513341] VFS: Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.513672] fuse init (API version 7.23)
[    0.513798] Key type big_key registered
[    0.514044] Key type asymmetric registered
[    0.514079] Asymmetric key parser 'x509' registered
[    0.514121] bounce: pool size: 64 pages
[    0.514174] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 249)
[    0.514239] io scheduler noop registered
[    0.514272] io scheduler deadline registered (default)
[    0.514324] io scheduler cfq registered
[    0.514702] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.514741] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.514802] intel_idle: MWAIT substates: 0x2120
[    0.514803] intel_idle: v0.4 model 0x3C
[    0.514804] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.514908] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.514961] ACPI: Power Button [PWRB]
[    0.515017] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.515067] ACPI: Power Button [PWRF]
[    0.515524] thermal LNXTHERM:00: registered as thermal_zone0
[    0.515559] ACPI: Thermal Zone [TZ00] (28 C)
[    0.515711] thermal LNXTHERM:01: registered as thermal_zone1
[    0.515746] ACPI: Thermal Zone [TZ01] (30 C)
[    0.515818] GHES: HEST is not enabled!
[    0.515858] isapnp: Scanning for PnP cards...
[    0.869036] isapnp: No Plug & Play device found
[    0.869213] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.871222] Linux agpgart interface v0.103
[    0.872587] brd: module loaded
[    0.873170] loop: module loaded
[    0.873347] libphy: Fixed MDIO Bus: probed
[    0.873381] tun: Universal TUN/TAP device driver, 1.6
[    0.873415] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.873478] PPP generic driver version 2.4.2
[    0.873613] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.873651] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 1
[    0.873775] xhci_hcd 0000:00:14.0: hcc params 0x200077c1 hci version 0x100 quirks 0x00009810
[    0.873833] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    0.873890] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.873926] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.873975] usb usb1: Product: xHCI Host Controller
[    0.874009] usb usb1: Manufacturer: Linux 4.2.0-997-generic xhci-hcd
[    0.874044] usb usb1: SerialNumber: 0000:00:14.0
[    0.874147] hub 1-0:1.0: USB hub found
[    0.874190] hub 1-0:1.0: 12 ports detected
[    0.876143] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.876179] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 2
[    0.876254] usb usb2: New USB device found, idVendor=1d6b, idProduct=0003
[    0.876290] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.876339] usb usb2: Product: xHCI Host Controller
[    0.876372] usb usb2: Manufacturer: Linux 4.2.0-997-generic xhci-hcd
[    0.876408] usb usb2: SerialNumber: 0000:00:14.0
[    0.876504] hub 2-0:1.0: USB hub found
[    0.876545] hub 2-0:1.0: 6 ports detected
[    0.877302] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.877341] ehci-pci: EHCI PCI platform driver
[    0.877427] ehci-pci 0000:00:1a.0: EHCI Host Controller
[    0.877463] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.877520] ehci-pci 0000:00:1a.0: debug port 2
[    0.881444] ehci-pci 0000:00:1a.0: cache line size of 64 is not supported
[    0.881450] ehci-pci 0000:00:1a.0: irq 16, io mem 0xf7c18000
[    0.893095] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    0.893154] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    0.893191] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.893240] usb usb3: Product: EHCI Host Controller
[    0.893273] usb usb3: Manufacturer: Linux 4.2.0-997-generic ehci_hcd
[    0.893308] usb usb3: SerialNumber: 0000:00:1a.0
[    0.893414] hub 3-0:1.0: USB hub found
[    0.893447] hub 3-0:1.0: 2 ports detected
[    0.893600] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    0.893636] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 4
[    0.893692] ehci-pci 0000:00:1d.0: debug port 2
[    0.897617] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    0.897622] ehci-pci 0000:00:1d.0: irq 23, io mem 0xf7c17000
[    0.909125] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    0.909188] usb usb4: New USB device found, idVendor=1d6b, idProduct=0002
[    0.909225] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.909273] usb usb4: Product: EHCI Host Controller
[    0.909307] usb usb4: Manufacturer: Linux 4.2.0-997-generic ehci_hcd
[    0.909342] usb usb4: SerialNumber: 0000:00:1d.0
[    0.909527] hub 4-0:1.0: USB hub found
[    0.909562] hub 4-0:1.0: 2 ports detected
[    0.909674] ehci-platform: EHCI generic platform driver
[    0.909713] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.909750] ohci-pci: OHCI PCI platform driver
[    0.909789] ohci-platform: OHCI generic platform driver
[    0.909827] uhci_hcd: USB Universal Host Controller Interface driver
[    0.909895] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    0.912092] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.912129] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.912394] mousedev: PS/2 mouse device common for all mice
[    0.912707] rtc_cmos 00:02: RTC can wake from S4
[    0.912850] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    0.912906] rtc_cmos 00:02: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    0.912960] i2c /dev entries driver
[    0.913024] device-mapper: uevent: version 1.0.3
[    0.913105] device-mapper: ioctl: 4.32.0-ioctl (2015-6-26) initialised: dm-devel@redhat.com
[    0.913170] platform eisa.0: Probing EISA bus 0
[    0.913203] platform eisa.0: EISA: Cannot allocate resource for mainboard
[    0.913239] platform eisa.0: Cannot allocate resource for EISA slot 1
[    0.913275] platform eisa.0: Cannot allocate resource for EISA slot 2
[    0.913311] platform eisa.0: Cannot allocate resource for EISA slot 3
[    0.913347] platform eisa.0: Cannot allocate resource for EISA slot 4
[    0.913383] platform eisa.0: Cannot allocate resource for EISA slot 5
[    0.913419] platform eisa.0: Cannot allocate resource for EISA slot 6
[    0.913455] platform eisa.0: Cannot allocate resource for EISA slot 7
[    0.913491] platform eisa.0: Cannot allocate resource for EISA slot 8
[    0.913527] platform eisa.0: EISA: Detected 0 cards
[    0.913570] cpufreq-nforce2: No nForce2 chipset.
[    0.913606] Intel P-state driver initializing.
[    0.913740] ledtrig-cpu: registered to indicate activity on CPUs
[    0.913845] PCCT header not found.
[    0.914445] NET: Registered protocol family 10
[    0.914954] NET: Registered protocol family 17
[    0.915046] Key type dns_resolver registered
[    0.915662] Using IPI No-Shortcut mode
[    0.916319] Loading compiled-in X.509 certificates
[    0.922021] Loaded X.509 cert 'Build time autogenerated kernel key: af8a9d2ee415a4a21dad7ea5fd0cfe1a66e294dc'
[    0.922087] registered taskstats version 1
[    0.922131] zswap: loading zswap
[    0.922882] zswap: using zbud pool
[    0.922914] zswap: using lzo compressor
[    0.924194] Key type trusted registered
[    0.926365] Key type encrypted registered
[    0.926401] AppArmor: AppArmor sha1 policy hashing enabled
[    0.926438] ima: No TPM chip found, activating TPM-bypass!
[    0.926484] evm: HMAC attrs: 0x1
[    0.926819]   Magic number: 11:493:583
[    0.926870] pci_bus 0000:04: hash matches
[    0.926946] rtc_cmos 00:02: setting system clock to 2015-08-29 12:34:44 UTC (1440851684)
[    0.927031] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.927066] EDD information not available.
[    0.927156] PM: Hibernation image not present or could not be loaded.
[    0.927287] Freeing unused kernel memory: 964K (c1ab8000 - c1ba9000)
[    0.927352] Write protecting the kernel text: 7168k
[    0.927429] Write protecting the kernel read-only data: 3068k
[    0.927464] NX-protecting the kernel data: 5120k
[    0.935089] systemd-udevd[99]: starting version 204
[    0.950268] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    0.950310] r8169 0000:05:00.0: can't disable ASPM; OS doesn't have ASPM control
[    0.957956] r8169 0000:05:00.0 eth0: RTL8168g/8111g at 0xf8426000, d4:3d:7e:f0:ce:83, XID 0c000800 IRQ 26
[    0.958012] r8169 0000:05:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    0.958727] [drm] Initialized drm 1.1.0 20060810
[    0.962311] sata_mv 0000:06:00.0: version 1.28
[    0.962380] sata_mv: Highpoint RocketRAID BIOS CORRUPTS DATA on all attached drives, regardless of if/how they are configured. BEWARE!
[    0.962438] sata_mv: For data safety, do not use sectors 8-9 on "Legacy" drives, and avoid the final two gigabytes on all RocketRAID BIOS initialized drives.
[    0.962553] sata_mv 0000:06:00.0: Gen-IIE 32 slots 4 ports SCSI mode IRQ via INTx
[    0.969389] ahci 0000:00:1f.2: version 3.0
[    0.969506] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x33 impl SATA mode
[    0.969559] ahci 0000:00:1f.2: flags: 64bit ncq led clo pio slum part ems apst 
[    0.972446] wmi: Mapper loaded
[    0.975207] megasas: 06.807.10.00-rc1
[    0.988225] scsi host0: sata_mv
[    0.990215] megasas: FW now in Ready state
[    0.990251] megaraid_sas 0000:02:0e.0: firmware supports msix	: (0)
[    0.990288] megaraid_sas 0000:02:0e.0: current msix/online cpus	: (0/2)
[    0.993012] scsi host2: sata_mv
[    0.994247] scsi host4: ahci
[    0.994383] scsi host3: sata_mv
[    0.994455] scsi host5: ahci
[    0.994536] scsi host6: sata_mv
[    0.994598] ata1: SATA max UDMA/133 mmio m1048576@0xf7800000 port 0xf7822000 irq 19
[    0.994652] ata2: SATA max UDMA/133 mmio m1048576@0xf7800000 port 0xf7824000 irq 19
[    0.994706] ata3: SATA max UDMA/133 mmio m1048576@0xf7800000 port 0xf7826000 irq 19
[    0.994758] ata4: SATA max UDMA/133 mmio m1048576@0xf7800000 port 0xf7828000 irq 19
[    0.995300] scsi host7: ahci
[    0.995392] scsi host8: ahci
[    0.995479] scsi host9: ahci
[    0.995583] scsi host10: ahci
[    0.995648] ata5: SATA max UDMA/133 abar m2048@0xf7c16000 port 0xf7c16100 irq 27
[    0.995702] ata6: SATA max UDMA/133 abar m2048@0xf7c16000 port 0xf7c16180 irq 27
[    0.995755] ata7: DUMMY
[    0.995785] ata8: DUMMY
[    0.995818] ata9: SATA max UDMA/133 abar m2048@0xf7c16000 port 0xf7c16300 irq 27
[    0.995871] ata10: SATA max UDMA/133 abar m2048@0xf7c16000 port 0xf7c16380 irq 27
[    0.996703] [drm] Memory usable by graphics device = 2048M
[    0.996810] [drm] Replacing VGA console driver
[    0.997611] Console: switching to colour dummy device 80x25
[    1.003169] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    1.003172] [drm] Driver supports precise vblank timestamp query.
[    1.003228] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    1.018657] r8169 0000:05:00.0 p2p1: renamed from eth0
[    1.029192] systemd-udevd[103]: renamed network interface eth0 to p2p1
[    1.061126] megaraid_sas 0000:02:0e.0: controller type	: MR(256MB)
[    1.061131] megasas_init_mfi: fw_support_ieee=0
[    1.061133] megasas: INIT adapter done
[    1.061138] megaraid_sas: fw state:c0000000
[    1.061139] megasas: fwstate:c0000000, dis_OCR=1
[    1.073157] [drm:drm_calc_timestamping_constants [drm]] *ERROR* crtc 21: Can't calculate constants, dotclock = 0!
[    1.078610] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    1.078911] acpi device:60: registered as cooling_device7
[    1.078965] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input4
[    1.079091] [drm] Initialized i915 1.6.0 20150717 for 0000:00:02.0 on minor 0
[    1.113614] fbcon: inteldrmfb (fb0) is primary device
[    1.133136] megaraid_sas 0000:02:0e.0: pci id		: (0x1000)/(0x0411)/(0x1000)/(0x1008)
[    1.133137] megaraid_sas 0000:02:0e.0: unevenspan support	: no
[    1.133138] megaraid_sas 0000:02:0e.0: disable ocr		: no
[    1.133138] megaraid_sas 0000:02:0e.0: firmware crash dump	: no
[    1.133139] megaraid_sas 0000:02:0e.0: secure jbod		: no
[    1.133141] scsi host1: Avago SAS based MegaRAID driver
[    1.134680] scsi 1:2:0:0: Direct-Access     LSI      MegaRAID 84016E  1.12 PQ: 0 ANSI: 5
[    1.135172] scsi 1:2:1:0: Direct-Access     LSI      MegaRAID 84016E  1.12 PQ: 0 ANSI: 5
[    1.140325] sd 1:2:0:0: [sda] 3904294912 512-byte logical blocks: (1.99 TB/1.81 TiB)
[    1.140328] sd 1:2:0:0: Attached scsi generic sg0 type 0
[    1.140418] sd 1:2:0:0: [sda] Write Protect is off
[    1.140419] sd 1:2:0:0: [sda] Mode Sense: 1f 00 10 08
[    1.140476] sd 1:2:0:0: [sda] Write cache: disabled, read cache: disabled, supports DPO and FUA
[    1.140508] sd 1:2:1:0: Attached scsi generic sg1 type 0
[    1.140567] sd 1:2:1:0: [sdb] 3904294912 512-byte logical blocks: (1.99 TB/1.81 TiB)
[    1.140651] sd 1:2:1:0: [sdb] Write Protect is off
[    1.140652] sd 1:2:1:0: [sdb] Mode Sense: 1f 00 10 08
[    1.140714] sd 1:2:1:0: [sdb] Write cache: disabled, read cache: disabled, supports DPO and FUA
[    1.141073]  sda: sda1
[    1.141292]  sdb: sdb1
[    1.141364] sd 1:2:0:0: [sda] Attached SCSI disk
[    1.141557] sd 1:2:1:0: [sdb] Attached SCSI disk
[    1.189095] usb 1-7: new low-speed USB device number 2 using xhci_hcd
[    1.194560] Console: switching to colour frame buffer device 240x67
[    1.199642] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[    1.199665] i915 0000:00:02.0: registered panic notifier
[    1.205139] usb 3-1: new high-speed USB device number 2 using ehci-pci
[    1.221122] usb 4-1: new high-speed USB device number 2 using ehci-pci
[    1.313149] ata1: SATA link down (SStatus 0 SControl 300)
[    1.320302] usb 1-7: New USB device found, idVendor=2635, idProduct=0601
[    1.320329] usb 1-7: New USB device strings: Mfr=0, Product=1, SerialNumber=0
[    1.320355] usb 1-7: Product:  2.4G RF MOUSE
[    1.320497] usb 1-7: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
[    1.321102] ata6: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.321140] ata9: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.321177] ata10: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.321562] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20150619/psargs-359)
[    1.321600] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT5._GTF] (Node f30a3c90), AE_NOT_FOUND (20150619/psparse-536)
[    1.321895] ata10.00: ATA-8: ST3000DM001-1CH166, CC24, max UDMA/133
[    1.321921] ata10.00: 5860533168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.322344] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20150619/psargs-359)
[    1.322381] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT5._GTF] (Node f30a3c90), AE_NOT_FOUND (20150619/psparse-536)
[    1.322662] ata10.00: configured for UDMA/133
[    1.325486] hidraw: raw HID events driver (C) Jiri Kosina
[    1.327408] ata6.00: ATA-8: SAMSUNG HD204UI, 1AQ10001, max UDMA/133
[    1.328563] ata6.00: 3907029168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.329736] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20150619/psargs-359)
[    1.330904] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT4._GTF] (Node f30a3c48), AE_NOT_FOUND (20150619/psparse-536)
[    1.332258] ata9.00: ATA-8: WDC WD20EARS-00J99B0, 80.00A80, max UDMA/133
[    1.333476] ata9.00: 3907029168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.333554] usbcore: registered new interface driver usbhid
[    1.333554] usbhid: USB HID core driver
[    1.337406] usb 3-1: New USB device found, idVendor=8087, idProduct=8008
[    1.338597] usb 3-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.339844] ata6.00: configured for UDMA/133
[    1.341924] hub 3-1:1.0: USB hub found
[    1.343144] hub 3-1:1.0: 6 ports detected
[    1.344488] input:  2.4G RF MOUSE as /devices/pci0000:00/0000:00:14.0/usb1/1-7/1-7:1.0/0003:2635:0601.0001/input/input6
[    1.345743] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20150619/psargs-359)
[    1.346971] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT4._GTF] (Node f30a3c48), AE_NOT_FOUND (20150619/psparse-536)
[    1.348351] hid-generic 0003:2635:0601.0001: input,hidraw0: USB HID v1.11 Mouse [ 2.4G RF MOUSE] on usb-0000:00:14.0-7/input0
[    1.349638] ata9.00: configured for UDMA/133
[    1.357543] usb 4-1: New USB device found, idVendor=8087, idProduct=8000
[    1.358809] usb 4-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.360292] hub 4-1:1.0: USB hub found
[    1.361672] hub 4-1:1.0: 6 ports detected
[    1.485125] usb 1-8: new low-speed USB device number 3 using xhci_hcd
[    1.509127] tsc: Refined TSC clocksource calibration: 3199.995 MHz
[    1.510355] clocksource: tsc: mask: 0xffffffffffffffff max_cycles: 0x2e20458adb9, max_idle_ns: 440795317868 ns
[    1.633146] ata2: SATA link down (SStatus 0 SControl 300)
[    1.642294] usb 1-8: New USB device found, idVendor=046d, idProduct=c30e
[    1.643558] usb 1-8: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.644827] usb 1-8: Product: HID compliant keyboard
[    1.646112] usb 1-8: Manufacturer: Logitech
[    1.647509] usb 1-8: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
[    1.648795] usb 1-8: ep 0x82 - rounding interval to 64 microframes, ep desc says 80 microframes
[    1.661179] input: Logitech HID compliant keyboard as /devices/pci0000:00/0000:00:14.0/usb1/1-8/1-8:1.0/0003:046D:C30E.0002/input/input7
[    1.717289] hid-generic 0003:046D:C30E.0002: input,hidraw1: USB HID v1.10 Keyboard [Logitech HID compliant keyboard] on usb-0000:00:14.0-8/input0
[    1.735692] input: Logitech HID compliant keyboard as /devices/pci0000:00/0000:00:14.0/usb1/1-8/1-8:1.1/0003:046D:C30E.0003/input/input8
[    1.789285] hid-generic 0003:046D:C30E.0003: input,hidraw2: USB HID v1.10 Device [Logitech HID compliant keyboard] on usb-0000:00:14.0-8/input1
[    1.953151] ata3: SATA link down (SStatus 0 SControl 300)
[    2.273149] ata4: SATA link down (SStatus 0 SControl 300)
[    2.509254] clocksource: Switched to clocksource tsc
[    3.213122] ata5: SATA link down (SStatus 1 SControl 300)
[    3.214649] scsi 5:0:0:0: Direct-Access     ATA      SAMSUNG HD204UI  0001 PQ: 0 ANSI: 5
[    3.216264] sd 5:0:0:0: Attached scsi generic sg2 type 0
[    3.216267] sd 5:0:0:0: [sdc] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
[    3.216284] sd 5:0:0:0: [sdc] Write Protect is off
[    3.216285] sd 5:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    3.216292] sd 5:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.221999] scsi 9:0:0:0: Direct-Access     ATA      WDC WD20EARS-00J 0A80 PQ: 0 ANSI: 5
[    3.223546] sd 9:0:0:0: Attached scsi generic sg3 type 0
[    3.223546] sd 9:0:0:0: [sdd] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
[    3.223548] sd 9:0:0:0: [sdd] 4096-byte physical blocks
[    3.223564] sd 9:0:0:0: [sdd] Write Protect is off
[    3.223565] sd 9:0:0:0: [sdd] Mode Sense: 00 3a 00 00
[    3.223572] sd 9:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.227793]  sdd: sdd1 sdd2
[    3.227948] sd 9:0:0:0: [sdd] Attached SCSI disk
[    3.233523] scsi 10:0:0:0: Direct-Access     ATA      ST3000DM001-1CH1 CC24 PQ: 0 ANSI: 5
[    3.235084] sd 10:0:0:0: [sde] 5860533168 512-byte logical blocks: (3.00 TB/2.72 TiB)
[    3.235094] sd 10:0:0:0: Attached scsi generic sg4 type 0
[    3.237929] sd 10:0:0:0: [sde] 4096-byte physical blocks
[    3.239388] sd 10:0:0:0: [sde] Write Protect is off
[    3.240801] sd 10:0:0:0: [sde] Mode Sense: 00 3a 00 00
[    3.240808] sd 10:0:0:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.253845]  sdc: sdc1 sdc2
[    3.255530] sd 5:0:0:0: [sdc] Attached SCSI disk
[    3.263847]  sde: sde1 sde2 sde3
[    3.265609] sd 10:0:0:0: [sde] Attached SCSI disk
[   26.161251] random: nonblocking pool is initialized
[   53.951865] ata5: exception Emask 0x10 SAct 0x0 SErr 0x4040000 action 0xe frozen
[   53.953157] ata5: irq_stat 0x00000040, connection status changed
[   53.954442] ata5: SError: { CommWake DevExch }
[   53.955728] ata5: hard resetting link
[   54.681044] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   55.757007] ata5.00: ATA-8: Corsair CSSD-F60GB2, 2.0, max UDMA/133
[   55.758272] ata5.00: 117231408 sectors, multi 1: LBA48 NCQ (depth 31/32), AA
[   55.804866] ata5.00: configured for UDMA/133
[   55.806097] ata5: EH complete
[   55.807342] scsi 4:0:0:0: Direct-Access     ATA      Corsair CSSD-F60 2.0  PQ: 0 ANSI: 5
[   55.808654] sd 4:0:0:0: [sdf] 117231408 512-byte logical blocks: (60.0 GB/55.8 GiB)
[   55.809924] sd 4:0:0:0: Attached scsi generic sg5 type 0
[   55.810393] sd 4:0:0:0: [sdf] Write Protect is off
[   55.810394] sd 4:0:0:0: [sdf] Mode Sense: 00 3a 00 00
[   55.810401] sd 4:0:0:0: [sdf] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   55.812367]  sdf: sdf1 sdf2 < sdf5 >
[   55.812513] sd 4:0:0:0: [sdf] Attached SCSI disk
[   76.287780] EXT4-fs (dm-0): mounted filesystem with ordered data mode. Opts: (null)
[   76.394765] init: plymouth-upstart-bridge main process (294) terminated with status 1
[   76.395943] init: plymouth-upstart-bridge main process ended, respawning
[   76.401008] init: plymouth-upstart-bridge main process (302) terminated with status 1
[   76.402141] init: plymouth-upstart-bridge main process ended, respawning
[   76.406497] init: plymouth-upstart-bridge main process (307) terminated with status 1
[   76.407613] init: plymouth-upstart-bridge main process ended, respawning
[   76.417721] init: ureadahead main process (297) terminated with status 5
[   76.610700] EXT4-fs (dm-0): re-mounted. Opts: errors=remount-ro
[   76.670953] EXT4-fs (sde3): mounted filesystem with ordered data mode. Opts: (null)
[   76.674130] EXT4-fs (sdf1): mounting ext2 file system using the ext4 subsystem
[   76.676671] EXT4-fs (sdf1): mounted filesystem without journal. Opts: (null)
[   87.642224] systemd-udevd[583]: starting version 204
[   87.665397] FS-Cache: Loaded
[   87.685059] RPC: Registered named UNIX socket transport module.
[   87.685061] RPC: Registered udp transport module.
[   87.685062] RPC: Registered tcp transport module.
[   87.685063] RPC: Registered tcp NFSv4.1 backchannel transport module.
[   87.718751] FS-Cache: Netfs 'nfs' registered for caching
[   87.725997] lp: driver loaded but no devices found
[   87.763175] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   87.768828] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[   87.916982] init: avahi-cups-reload main process (702) terminated with status 1
[   87.994606] md: sda does not have a valid v1.2 superblock, not importing!
[   87.994616] md: md_import_device returned -22
[   87.994624] md: md0 stopped.
[   88.018257] md: bind<sdd>
[   88.039998] md: bind<sdc>
[   88.058827] md: sdb does not have a valid v1.2 superblock, not importing!
[   88.058835] md: md_import_device returned -22
[   88.120091] intel_rapl: Found RAPL domain package
[   88.120094] intel_rapl: Found RAPL domain core
[   88.120095] intel_rapl: Found RAPL domain uncore
[   88.120097] intel_rapl: Found RAPL domain dram
[   88.151205] md: bind<sde1>
[   88.155185] md: bind<sde2>
[   88.181609] audit: type=1400 audit(1440851771.751:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=888 comm="apparmor_parser"
[   88.181613] audit: type=1400 audit(1440851771.751:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=888 comm="apparmor_parser"
[   88.181616] audit: type=1400 audit(1440851771.751:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=888 comm="apparmor_parser"
[   88.181884] audit: type=1400 audit(1440851771.751:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=888 comm="apparmor_parser"
[   88.181887] audit: type=1400 audit(1440851771.751:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=888 comm="apparmor_parser"
[   88.182016] audit: type=1400 audit(1440851771.751:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=888 comm="apparmor_parser"
[   88.196176] snd_hda_intel 0000:00:03.0: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915])
[   88.264933] input: HDA Intel HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:03.0/sound/card0/input9
[   88.264991] input: HDA Intel HDMI HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:03.0/sound/card0/input10
[   88.265120] input: HDA Intel HDMI HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:03.0/sound/card0/input11
[   88.286604] r8169 0000:05:00.0 p2p1: link down
[   88.286623] r8169 0000:05:00.0 p2p1: link down
[   88.289127] IPv6: ADDRCONF(NETDEV_UP): p2p1: link is not ready
[   88.393514] init: Failed to obtain startpar-bridge instance: Unknown parameter: INSTANCE
[   88.483504] init: samba-ad-dc main process (1135) terminated with status 1
[   88.774739] Adding 3407868k swap on /dev/mapper/cryptswap1.  Priority:-1 extents:1 across:3407868k SSFS
[   90.947054] r8169 0000:05:00.0 p2p1: link up
[   90.947060] IPv6: ADDRCONF(NETDEV_CHANGE): p2p1: link becomes ready
[  208.399234] audit: type=1400 audit(1440851891.967:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=2385 comm="apparmor_parser"
[  208.399239] audit: type=1400 audit(1440851891.967:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=2385 comm="apparmor_parser"
[  208.399242] audit: type=1400 audit(1440851891.967:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=2385 comm="apparmor_parser"
[  208.399507] audit: type=1400 audit(1440851891.967:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=2385 comm="apparmor_parser"
[  208.399509] audit: type=1400 audit(1440851891.967:12): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=2385 comm="apparmor_parser"
[  208.399638] audit: type=1400 audit(1440851891.967:13): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=2385 comm="apparmor_parser"
[  208.402546] audit: type=1400 audit(1440851891.971:14): apparmor="STATUS" operation="profile_load" name="/usr/bin/freshclam" pid=2387 comm="apparmor_parser"
[  208.403039] audit: type=1400 audit(1440851891.971:15): apparmor="STATUS" operation="profile_load" name="/usr/sbin/clamd" pid=2388 comm="apparmor_parser"
[  208.404453] audit: type=1400 audit(1440851891.971:16): apparmor="STATUS" operation="profile_load" name="/usr/sbin/named" pid=2389 comm="apparmor_parser"
[  208.405848] audit: type=1400 audit(1440851891.975:17): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=2391 comm="apparmor_parser"
[  214.808651] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[  214.808822] NFSD: starting 90-second grace period (net c1a8b380)
[  222.228987] ipmi message handler version 39.2
[  222.236036] IPMI System Interface driver.
[  222.236057] ipmi_si: Adding default-specified kcs state machine
[  222.236059] ipmi_si: Trying default-specified kcs state machine at i/o address 0xca2, slave address 0x0, irq 0
[  222.236062] ipmi_si: Interface detection failed
[  222.244851] ipmi_si: Adding default-specified smic state machine
[  222.244854] ipmi_si: Trying default-specified smic state machine at i/o address 0xca9, slave address 0x0, irq 0
[  222.244857] ipmi_si: Interface detection failed
[  222.256783] ipmi_si: Adding default-specified bt state machine
[  222.256786] ipmi_si: Trying default-specified bt state machine at i/o address 0xe4, slave address 0x0, irq 0
[  222.256789] ipmi_si: Interface detection failed
[  222.268801] ipmi_si: Unable to find any System Interface(s)
[  224.047846] ip_tables: (C) 2000-2006 Netfilter Core Team
[  224.079973] md: bind<sda1>
[  224.108176] md: bind<sdb1>
[  224.293227] init: plymouth-upstart-bridge main process ended, respawning
[  251.527223] md: md0 stopped.
[  251.527229] md: unbind<sdc>
[  251.540754] md: export_rdev(sdc)
[  251.540792] md: unbind<sdd>
[  251.552740] md: export_rdev(sdd)
[  252.655268] md: md1 stopped.
[  252.655273] md: unbind<sde2>
[  252.664763] md: export_rdev(sde2)
[  255.538416] md: md1 stopped.
[  255.540015] md: bind<sdd2>
[  255.541025] md: bind<sde2>
[  255.541158] md: bind<sdc2>
[  255.547356] md: raid0 personality registered for level 0
[  255.547847] md/raid0:md1: md_size is 8196096 sectors.
[  255.547849] md: RAID0 configuration for md1 - 1 zone
[  255.547850] md: zone0=[sdc2/sdd2/sde2]
[  255.547853]       zone-offset=         0KB, device-offset=         0KB, size=   4098048KB
[  255.547853] 
[  255.547870] md1: detected capacity change from 0 to 4196401152
[  255.662475] md: array md127 already has disks!
[  255.662566] md: bind<sdc1>
[  255.662672] md: bind<sdd1>
[  255.736711] raid6: mmxx1    gen()  6194 MB/s
[  255.804717] raid6: mmxx2    gen()  6317 MB/s
[  255.872718] raid6: sse1x1   gen()  5181 MB/s
[  255.940708] raid6: sse1x2   gen()  6284 MB/s
[  256.008708] raid6: sse2x1   gen() 10553 MB/s
[  256.076711] raid6: sse2x1   xor()  7704 MB/s
[  256.144712] raid6: sse2x2   gen() 12795 MB/s
[  256.212709] raid6: sse2x2   xor()  8328 MB/s
[  256.212710] raid6: using algorithm sse2x2 gen() 12795 MB/s
[  256.212711] raid6: .... xor() 8328 MB/s, rmw enabled
[  256.212712] raid6: using ssse3x1 recovery algorithm
[  256.215292] async_tx: api initialized (async)
[  256.218224] xor: measuring software checksum speed
[  256.256696]    pIII_sse  : 19636.000 MB/sec
[  256.296696]    prefetch64-sse: 21713.000 MB/sec
[  256.296697] xor: using function: prefetch64-sse (21713.000 MB/sec)
[  256.311873] md: raid6 personality registered for level 6
[  256.311875] md: raid5 personality registered for level 5
[  256.311876] md: raid4 personality registered for level 4
[  256.312044] md/raid:md127: device sdd1 operational as raid disk 2
[  256.312045] md/raid:md127: device sdc1 operational as raid disk 1
[  256.312046] md/raid:md127: device sdb1 operational as raid disk 0
[  256.312047] md/raid:md127: device sda1 operational as raid disk 4
[  256.312048] md/raid:md127: device sde1 operational as raid disk 3
[  256.312274] md/raid:md127: allocated 5317kB
[  256.312285] md/raid:md127: raid level 6 active with 5 out of 5 devices, algorithm 2
[  256.312285] RAID conf printout:
[  256.312286]  --- level:6 rd:5 wd:5
[  256.312287]  disk 0, o:1, dev:sdb1
[  256.312288]  disk 1, o:1, dev:sdc1
[  256.312289]  disk 2, o:1, dev:sdd1
[  256.312289]  disk 3, o:1, dev:sde1
[  256.312290]  disk 4, o:1, dev:sda1
[  256.312373] created bitmap (15 pages) for device md127
[  256.313949] md127: bitmap initialized from disk: read 1 pages, set 2 of 29786 bits
[  256.735926] md127: detected capacity change from 0 to 5996591185920
[  259.718689] EXT4-fs (md127): mounted filesystem with ordered data mode. Opts: (null)
[ 1227.289838] EXT4-fs (md1): mounted filesystem with ordered data mode. Opts: (null)
[ 3761.957086] EXT4-fs (dm-0): re-mounted. Opts: errors=remount-ro,discard,discard
[ 3780.857992] EXT4-fs (sdf1): re-mounted. Opts: discard
[ 4020.583292] SGI XFS with ACLs, security attributes, realtime, no debug enabled
[ 4020.593954] JFS: nTxBlock = 8192, nTxLock = 65536
[ 4020.607715] ntfs: driver 2.1.32 [Flags: R/O MODULE].
[ 4020.629471] QNX4 filesystem 0.2.3 registered.
[ 4020.667155] Btrfs loaded

```

So basically, I boot the system fine, only to find /dev/md0 and /dev/md1 which are not usable (assembled incorrectly). I mdadm --stop both of them, then mdadm --assemble --scan, and they assemble just fine.

Any ideas?

Thanks

---

