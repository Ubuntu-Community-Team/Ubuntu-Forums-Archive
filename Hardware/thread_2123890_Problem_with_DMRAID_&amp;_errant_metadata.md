---
title: "Problem with DMRAID &amp; errant metadata"
date: 2013-03-09
forum: Hardware
---

### Post by markius on 2013-03-09
Quantal. MSI motherboard with SB700 chipset. RAID1 mirror shows as degraded

Looks like /dev/sda has 2 different types of RAID metadata.

```
root@ubuntu:~# dmraid -n /dev/sda
/dev/sda: "pdc" and "ddf1" formats discovered (using ddf1)!
/dev/sda (ddf1):
DDF1 anchor at 1953525167 with tables in big-endian format.
DDF1 Header at 0x8ebc378
0x000 signature:        0xDE11DE11
0x004 crc:              0x84773785
0x008 guid:             "Dell    .(...(..84F.$..." [44 65 6c 6c 20 20 20 20 10 28 00 15 10 28 1f 02 38 34 46 b7 24 cb 1e e2]
0x020 rev:              "01.00.00" [30 31 2e 30 30 2e 30 30]
0x028 seqnum:           -1
0x02c timestamp:        0x38344842
0x030 open:             0x0
0x031 foreign:          0x0
0x032 grouping:         0x1
0x060 primary header:   1953516747
0x068 secondary header: 1953508327
0x070 header type:      0x0
0x074 workspace len:    32684
0x078 workspace lba:    1952476592
0x080 max pd:           255
0x082 max vd:           255
0x084 max part:         16
0x086 vd_config len:    7
0x088 max_primary_elts: 256
0x0c0 adapter_offset:   1
0x0c4 adapter_len:      1
0x0c8 pd_offset:        2
0x0cc pd_len:           32
0x0d0 vd_offset:        34
0x0d4 vd_len:           32
0x0d8 config_offset:    66
0x0dc config_len:       119
0x0e0 disk_data_offset: 185
0x0e4 disk_data_len:    1
0x0e8 badblock_offset:  186
0x0ec badblock_len:     8
0x0f0 diag_offset:      -1
0x0f4 diag_len:         0
0x0f8 vendor_offset:    -1
0x0fc vendor_len:       0
DDF1 Header at 0x8ebc5b8
0x000 signature:        0xDE11DE11
0x004 crc:              0x73B101C0
0x008 guid:             "Dell    .(...(..84F.$..." [44 65 6c 6c 20 20 20 20 10 28 00 15 10 28 1f 02 38 34 46 b7 24 cb 1e e2]
0x020 rev:              "01.00.00" [30 31 2e 30 30 2e 30 30]
0x028 seqnum:           8
0x02c timestamp:        0x38346FC0
0x030 open:             0x0
0x031 foreign:          0x0
0x032 grouping:         0x1
0x060 primary header:   1953516747
0x068 secondary header: 1953508327
0x070 header type:      0x1
0x074 workspace len:    32684
0x078 workspace lba:    1952476592
0x080 max pd:           255
0x082 max vd:           255
0x084 max part:         16
0x086 vd_config len:    7
0x088 max_primary_elts: 256
0x0c0 adapter_offset:   1
0x0c4 adapter_len:      1
0x0c8 pd_offset:        2
0x0cc pd_len:           32
0x0d0 vd_offset:        34
0x0d4 vd_len:           32
0x0d8 config_offset:    66
0x0dc config_len:       119
0x0e0 disk_data_offset: 185
0x0e4 disk_data_len:    1
0x0e8 badblock_offset:  186
0x0ec badblock_len:     8
0x0f0 diag_offset:      -1
0x0f4 diag_len:         0
0x0f8 vendor_offset:    -1
0x0fc vendor_len:       0
DDF1 Header at 0x8ebc7c0
0x000 signature:        0xDE11DE11
0x004 crc:              0x34568D4E
0x008 guid:             "Dell    .(...(..84F.$..." [44 65 6c 6c 20 20 20 20 10 28 00 15 10 28 1f 02 38 34 46 b7 24 cb 1e e2]
0x020 rev:              "01.00.00" [30 31 2e 30 30 2e 30 30]
0x028 seqnum:           8
0x02c timestamp:        0x38346FC0
0x030 open:             0x0
0x031 foreign:          0x0
0x032 grouping:         0x1
0x060 primary header:   1953516747
0x068 secondary header: 1953508327
0x070 header type:      0x2
0x074 workspace len:    32684
0x078 workspace lba:    1952476592
0x080 max pd:           255
0x082 max vd:           255
0x084 max part:         16
0x086 vd_config len:    7
0x088 max_primary_elts: 256
0x0c0 adapter_offset:   1
0x0c4 adapter_len:      1
0x0c8 pd_offset:        2
0x0cc pd_len:           32
0x0d0 vd_offset:        34
0x0d4 vd_len:           32
0x0d8 config_offset:    66
0x0dc config_len:       119
0x0e0 disk_data_offset: 185
0x0e4 disk_data_len:    1
0x0e8 badblock_offset:  186
0x0ec badblock_len:     8
0x0f0 diag_offset:      -1
0x0f4 diag_len:         0
0x0f8 vendor_offset:    -1
0x0fc vendor_len:       0
Adapter Data at 0x8ebc9c8
0x000 signature:        0xAD111111
0x004 crc:              0xAB30E76
0x008 guid:             "Dell    12345..........." [44 65 6c 6c 20 20 20 20 31 32 33 34 35 00 00 00 00 00 00 00 00 00 00 8b]
0x020 pci vendor:       0x1028
0x022 pci device:       0x15
0x024 pci subvendor:    0x1028
0x026 pci subdevice:    0x1F02
Disk Data at 0x8ebcbd0
0x000 signature:        0x33333333
0x004 crc:              0x6B3D7EAA
0x008 guid:             "ATA 200911172165a4591152" [41 54 41 20 32 30 30 39 31 31 31 37 32 31 36 35 61 34 35 39 31 31 35 32]
0x020 reference:                0xDD2C50F9
0x024 forced_ref_flag:  0
0x025 forced_guid_flag: 1
Physical Drive Header at 0x8ebcdd8
0x000 signature:        0x22222222
0x004 crc:              0x93AF3363
0x008 num drives:       6
0x00a max drives:       255
Physical Drive at 0x8ebce18
0x000 guid:             "ATA 99990101f356509c33e6" [41 54 41 20 39 39 39 39 30 31 30 31 66 33 35 36 35 30 39 63 33 33 65 36]
0x018 reference #:      0x49CD9A32
0x01c type:             0x3003
0x01e state:            0x1
0x020 size:             975699968
0x028 path info:        ".................." [00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00]
Physical Drive at 0x8ebce58
0x000 guid:             "ATA 99990101767b0af76804" [41 54 41 20 39 39 39 39 30 31 30 31 37 36 37 62 30 61 66 37 36 38 30 34]
0x018 reference #:      0xD6947DA7
0x01c type:             0x3003
0x01e state:            0x1
0x020 size:             623902720
0x028 path info:        ".................." [00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00]
Physical Drive at 0x8ebce98
0x000 guid:             "ATA 99990101c0c0706e51e1" [41 54 41 20 39 39 39 39 30 31 30 31 63 30 63 30 37 30 36 65 35 31 65 31]
0x018 reference #:      0xF1A5D471
0x01c type:             0x3003
0x01e state:            0x1
0x020 size:             975699968
0x028 path info:        ".................." [00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00]
Physical Drive at 0x8ebced8
0x000 guid:             "ATA 9999010158f750df8104" [41 54 41 20 39 39 39 39 30 31 30 31 35 38 66 37 35 30 64 66 38 31 30 34]
0x018 reference #:      0x4AD47C7B
0x01c type:             0x3003
0x01e state:            0x1
0x020 size:             975699968
0x028 path info:        ".................." [00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00]
Physical Drive at 0x8ebcf18
0x000 guid:             "ATA 999901017cda7627e147" [41 54 41 20 39 39 39 39 30 31 30 31 37 63 64 61 37 36 32 37 65 31 34 37]
0x018 reference #:      0xD43000AF
0x01c type:             0x3003
0x01e state:            0x1
0x020 size:             975699968
0x028 path info:        ".................." [00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00]
Physical Drive at 0x8ebcf58
0x000 guid:             "ATA 200911172165a4591152" [41 54 41 20 32 30 30 39 31 31 31 37 32 31 36 35 61 34 35 39 31 31 35 32]
0x018 reference #:      0xDD2C50F9
0x01c type:             0x3003
0x01e state:            0x1
0x020 size:             1952448512
0x028 path info:        ".................." [00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00]
Virtual Drive Header at 0x8ec0de0
0x000 signature:        0xDDDDDDDD
0x004 crc:              0xBA268F47
0x008 num drives:       3
0x00a max drives:       255
Virtual Drive at 0x8ec0e20
0x000 guid:             "Dell    .(...(..7(..!Rn." [44 65 6c 6c 20 20 20 20 10 28 00 15 10 28 1f 02 37 28 d7 89 21 52 6e e3]
0x018 vd #:             0x0
0x01c type:             0x2
0x020 state:            0x0
0x021 init state:       0x0
0x030 name:             "................" [00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00]
Virtual Drive at 0x8ec0e60
0x000 guid:             "Dell    .(...(..7(.h...." [44 65 6c 6c 20 20 20 20 10 28 00 15 10 28 1f 02 37 28 d7 68 84 f9 fa d3]
0x018 vd #:             0x0
0x01c type:             0x2
0x020 state:            0x0
0x021 init state:       0x0
0x030 name:             "................" [00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00]
Virtual Drive at 0x8ec0ea0
0x000 guid:             "Dell    .(...(..5..G..8." [44 65 6c 6c 20 20 20 20 10 28 00 15 10 28 1f 02 35 e6 95 47 e8 1a 38 9b]
0x018 vd #:             0x0
0x01c type:             0x2
0x020 state:            0x0
0x021 init state:       0x0
0x030 name:             "................" [00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00]
Virtual Drive Config Record at 0x8ec4de8
0x000 signature:        0xEEEEEEEE
0x004 crc:              0xA3669103
0x008 guid:             "Dell    .(...(..5..G..8." [44 65 6c 6c 20 20 20 20 10 28 00 15 10 28 1f 02 35 e6 95 47 e8 1a 38 9b]
0x020 timestamp:        0x35E69547
0x024 seqnum:           3
0x040 primary count:    4
0x042 stripe size:      7KiB
0x043 raid level:       5
0x044 raid qualifier:   3
0x045 secondary count:  1
0x046 secondary number: 0
0x047 secondary level:  0
0x060 spare 0:          0xFFFFFFFF
0x064 spare 1:          0xFFFFFFFF
0x068 spare 2:          0xFFFFFFFF
0x06c spare 3:          0xFFFFFFFF
0x070 spare 4:          0xFFFFFFFF
0x074 spare 5:          0xFFFFFFFF
0x078 spare 6:          0xFFFFFFFF
0x07c spare 7:          0xFFFFFFFF
0x080 cache policy:     0xFFFFFFFF
0x088 bg task rate:     255
0x048 sector count:     975699968
0x050 size:             2927099904
Drive map:
0: F1A5D471 @ 0
1: DD2C50F9 @ 0
2: 4AD47C7B @ 0
3: D43000AF @ 0
```

```
root@ubuntu:~# dmraid -n /dev/sda -f pdc
/dev/sda (pdc):
0x000 promise_id: "Promise Technology, Inc."
0x018 unknown_0: 0x20000 131072
0x01c magic_0: 0x513b16ee
0x020 unknown_1: 0x25d7 9687
0x024 magic_1: 0x513b16ee
0x028 unknown_2: 0x25d7 9687
0x200 raid.flags: 0xfdfeffc0
0x204 raid.unknown_0: 0x7 7
0x205 raid.disk_number: 0
0x206 raid.channel: 0
0x207 raid.device: 0
0x208 raid.magic_0: 0x4b033edd
0x20c raid.unknown_1: 0xe84e 59470
0x210 raid.start: 0x0 0
0x214 raid.disk_secs: 1953394096
0x218 raid.unknown_3: 0xffffffff 4294967295
0x21c raid.unknown_4: 0x79 121
0x21e raid.status: 0xf
0x21f raid.type: 0x1
0x220 raid.total_disks: 2
0x221 raid.raid0_shift: 7
0x222 raid.raid0_disks: 1
0x223 raid.array_number: 1
0x224 raid.total_secs: 1953124992
0x228 raid.cylinders: 65534
0x22a raid.heads: 254
0x22b raid.sectors: 63
0x22c raid.magic_1: 0xba410320
0x230 raid.unknown_5: 0x1000012 16777234
0x234 raid.disk[0].unknown_0: 0x7
0x236 raid.disk[0].channel: 0
0x237 raid.disk[0].device: 0
0x238 raid.disk[0].magic_0: 0x4b033edd
0x23c raid.disk[0].disk_number: 59470
0x240 raid.disk[1].unknown_0: 0x207
0x242 raid.disk[1].channel: 1
0x243 raid.disk[1].device: 0
0x244 raid.disk[1].magic_0: 0x4a61993e
0x248 raid.disk[1].disk_number: 109706
0x7fc checksum: 0x2368d008 Ok
```

Only pdc is correct for this system:

```
root@ubuntu:~# lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:03.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:09.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 4)
00:11.0 RAID bus controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [Non-RAID5 mode]
00:12.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.1 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0 USB OHCI1 Controller
00:12.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.1 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0 USB OHCI1 Controller
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 IDE Controller
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge
00:14.5 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:00.0 VGA compatible controller: NVIDIA Corporation GF108 [GeForce GT 430] (rev a1)
01:00.1 Audio device: NVIDIA Corporation GF108 High Definition Audio Controller (rev a1)
02:00.0 PCI bridge: PLX Technology, Inc. PEX 8604 4-lane, 4-Port PCI Express Gen 2 (5.0 GT/s) Switch (rev ba)
03:01.0 PCI bridge: PLX Technology, Inc. PEX 8604 4-lane, 4-Port PCI Express Gen 2 (5.0 GT/s) Switch (rev ba)
03:04.0 PCI bridge: PLX Technology, Inc. PEX 8604 4-lane, 4-Port PCI Express Gen 2 (5.0 GT/s) Switch (rev ba)
03:05.0 PCI bridge: PLX Technology, Inc. PEX 8604 4-lane, 4-Port PCI Express Gen 2 (5.0 GT/s) Switch (rev ba)
05:00.0 Multimedia controller: Philips Semiconductors SAA7231 (rev aa)
06:00.0 Multimedia controller: Philips Semiconductors SAA7231 (rev aa)
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
08:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller
```

```
root@ubuntu:~# dmraid -ay -f pdc
RAID set "pdc_dbceiccibg" was activated
RAID set "pdc_dbceiccibg1" was activated
```

```
root@ubuntu:~# dmraid -ay
/dev/sda: "pdc" and "ddf1" formats discovered (using ddf1)!
ERROR: ddf1: wrong # of devices in RAID set "ddf1_44656c6c202020201028001510281f0235e69547e81a389b" [1/4] on /dev/sda
ERROR: pdc: wrong # of devices in RAID set "pdc_dbceiccibg" [1/2] on /dev/sdb
ERROR: pdc: wrong # of devices in RAID set "pdc_dbceiccibg" [1/2] on /dev/sdb
RAID set "ddf1_44656c6c202020201028001510281f0235e69547e81a389b" was activated
ERROR: creating degraded mirror mapping for "pdc_dbceiccibg"
RAID set "pdc_dbceiccibg" was activated
ERROR: opening "/dev/mapper/ddf1_44656c6c202020201028001510281f0235e69547e81a389b"
RAID set "pdc_dbceiccibg1" was activated
```

How can I fix this?  Is it safe to do this:
```
dmraid -r -E -f ddf1 /dev/sda
```

---

### Post by markius on 2013-03-09
So I tried that command and it errors out:
```
ERROR: ddf1: seeking device "/dev/sda" to 512104901378048
ERROR: writing metadata to /dev/sda, offset 1000204885504 sectors, size 0 bytes returned 0
ERROR: erasing ondisk metadata on /dev/sda

```

---

### Post by markius on 2013-03-09
Solved with the help of SolarisBoy in IRC.

[COLOR="#FF0000"]**BE CAREFUL IF YOU'RE FOLLOWING THESE INSTRUCTIONS!!**[/COLOR]

dmraid revealed the offset of the errant ddf1 metadata to be 1953525167 512-byte sectors from the beginning of the disk [this turns out to be the last sector of the disk]

```
root@ubuntu:~# dmraid -n /dev/sda
/dev/sda: "pdc" and "ddf1" formats discovered (using ddf1)!
/dev/sda (ddf1):
DDF1 anchor at 1953525167 with tables in big-endian format.

```


I used DD to dump that block out as a backup:
```
dd if=/dev/sda of=/root/ddf1.metadata.backup skip=1953525167 bs=512 count=1
```

Then erased it with a block from /dev/zero
```
dd if=/dev/zero of=/dev/sda seek=1953525167 bs=512 count=1
```

After doing that only pdc metadata was found by dmraid:
```
root@ubuntu:~# dmraid -n /dev/sda
/dev/sda (pdc):
0x000 promise_id: "Promise Technology, Inc."
0x018 unknown_0: 0x20000 131072
0x01c magic_0: 0x513b16ee
0x020 unknown_1: 0x25d7 9687
0x024 magic_1: 0x513b16ee
0x028 unknown_2: 0x25d7 9687
0x200 raid.flags: 0xfdfeffc0
0x204 raid.unknown_0: 0x7 7
0x205 raid.disk_number: 0
0x206 raid.channel: 0
0x207 raid.device: 0
0x208 raid.magic_0: 0x4b033edd
0x20c raid.unknown_1: 0xe84e 59470
0x210 raid.start: 0x0 0
0x214 raid.disk_secs: 1953394096
0x218 raid.unknown_3: 0xffffffff 4294967295
0x21c raid.unknown_4: 0x79 121
0x21e raid.status: 0xf
0x21f raid.type: 0x1
0x220 raid.total_disks: 2
0x221 raid.raid0_shift: 7
0x222 raid.raid0_disks: 1
0x223 raid.array_number: 1
0x224 raid.total_secs: 1953124992
0x228 raid.cylinders: 65534
0x22a raid.heads: 254
0x22b raid.sectors: 63
0x22c raid.magic_1: 0xba410320
0x230 raid.unknown_5: 0x1000012 16777234
0x234 raid.disk[0].unknown_0: 0x7
0x236 raid.disk[0].channel: 0
0x237 raid.disk[0].device: 0
0x238 raid.disk[0].magic_0: 0x4b033edd
0x23c raid.disk[0].disk_number: 59470
0x240 raid.disk[1].unknown_0: 0x207
0x242 raid.disk[1].channel: 1
0x243 raid.disk[1].device: 0
0x244 raid.disk[1].magic_0: 0x4a61993e
0x248 raid.disk[1].disk_number: 109706
0x7fc checksum: 0x2368d008 Ok

```

---

### Post by markius on 2013-03-09
So why didn't dmraid remove the metadata when asked?  Because it's buggy.

ERROR: ddf1: seeking device "/dev/sda" to 512104901378048

512194891378048? What is that?  It's (2^16) * 1953525167 is what it is.

My guess is that dmraid is confused between sector and byte offsets:

ERROR: writing metadata to /dev/sda, offset 1000204885504 sectors
should be offset 1000204885504 **BYTES**

---

### Post by jsylvia007 on 2014-01-14
Sorry to wake up almost a year old thread, but I'm having the same issue with 12.04...  The issue I have is with isw and ddf1.  I can correctly kill the ddf1 using your above procedure with dd, but when I reboot to make sure everything is ok, the entire partition table of the RAID is dead, and all data is lost.  I needed to restore that sector from the backup, and reboot.  

What am I missing??!  It doesn't make any sense to me...  Is there another way I can fix this without losing all my data by DD-ing the WHOLE Drive and recreating the RAID from scratch?

My setup is 2 x 1TB drive in an intel raid 1...

---

### Post by markius on 2014-01-15
No problem from me with reviving an old thread!

I don't know anything about isw but I suspect that it stores its metadata in the same block as ddf1 so when you trash ddf1 using DD you also trash isw.  You may need to somehow edit the the block to remove only the ddf1 metadata although I don't know how you would actually do that.

Are you able to see any diagnostic informaiton that would indicate the byte offsets for the ddf1 and isw metadata?

M

---

### Post by jsylvia007 on 2014-01-15
I used the commands above to look for "anchor", but I couldn't find anything for ISW metadata...  

Shouldn't I be able to just completely DD the beginning and DD the end of the drive, and somehow force a rebuild of the array?  Why does it cause the whole array to fail...

Maybe what I can do is compare both of those blocks...  One on the "working" drive, and the one on the bad drive, and see what's there for data...  Could I just DD those blocks?  Is there reasonable expectation that the metadata is the same on both drives?

---

### Post by markius on 2014-01-15
Could you post the output of 

dmraid -n /dev/sda
dmraid -n /dev/sda -f isw

I think your problem with erasing the first/last sector of your disk is that one or other of them contains metadata for both isw and ddf.  If you clear the isw metadata the array controller has no way to know what the array should look like.  With two drives it could be either RAID1 or RAID0 and the controller needs the metadata to tell it which one.

Bear in mind this is all speculation on my part :)

---

### Post by markius on 2014-01-15
Perhaps the DMESG output would be useful too

---

### Post by jsylvia007 on 2014-01-15
Here is the requested output...

Just to note...  /dev/sdc is the "correct" drive with only ISW metadata, and /dev/sdb has both DDF1 and ISW...

DMESG:

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.2.0-58-generic (buildd@allspice) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #88-Ubuntu SMP Tue Dec 3 17:37:58 UTC 2013 (Ubuntu 3.2.0-58.88-generic 3.2.53)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-58-generic root=UUID=aa67efab-a30a-45f0-d228-60a73bc64935 ro
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000dfe8ac00 (usable)
[    0.000000]  BIOS-e820: 00000000dfe8ac00 - 00000000dfe8cc00 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000dfe8cc00 - 00000000dfe8ec00 (ACPI data)
[    0.000000]  BIOS-e820: 00000000dfe8ec00 - 00000000e4000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000feda0000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fef00000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 000000021c000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.3 present.
[    0.000000] DMI: Dell Inc.                 Precision WorkStation 380    /0CJ774, BIOS A09 01/08/2007
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x21c000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-D7FFF write-protect
[    0.000000]   D8000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 080000000 mask FC0000000 write-back
[    0.000000]   2 base 0C0000000 mask FE0000000 write-back
[    0.000000]   3 base 0DFF00000 mask FFFF00000 uncachable
[    0.000000]   4 base 100000000 mask F00000000 write-back
[    0.000000]   5 base 200000000 mask FE0000000 write-back
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3GB, range: 512MB, type WB
[    0.000000] reg 3, base: 3583MB, range: 1MB, type UC
[    0.000000] reg 4, base: 4GB, range: 4GB, type WB
[    0.000000] reg 5, base: 8GB, range: 512MB, type WB
[    0.000000] total RAM covered: 8191M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K 	chunk_size: 2M 	num_reg: 6  	lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3GB, range: 512MB, type WB
[    0.000000] reg 3, base: 3583MB, range: 1MB, type UC
[    0.000000] reg 4, base: 4GB, range: 4GB, type WB
[    0.000000] reg 5, base: 8GB, range: 512MB, type WB
[    0.000000] e820 update range: 00000000dff00000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xdfe8a max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [ffff8800000fe710] fe710
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Base memory trampoline at [ffff880000094000] 94000 size 20480
[    0.000000] init_memory_mapping: 0000000000000000-00000000dfe8a000
[    0.000000]  0000000000 - 00dfe00000 page 2M
[    0.000000]  00dfe00000 - 00dfe8a000 page 4k
[    0.000000] kernel direct mapping tables up to dfe8a000 @ 1fffa000-20000000
[    0.000000] init_memory_mapping: 0000000100000000-000000021c000000
[    0.000000]  0100000000 - 021c000000 page 2M
[    0.000000] kernel direct mapping tables up to 21c000000 @ dfe84000-dfe8a000
[    0.000000] RAMDISK: 3639e000 - 371c7000
[    0.000000] ACPI: RSDP 00000000000feb00 00024 (v02 DELL  )
[    0.000000] ACPI: XSDT 00000000000fd25e 00074 (v01 DELL    WS 380  00000007 ASL  00000061)
[    0.000000] ACPI: FACP 00000000000fd356 000F4 (v03 DELL    WS 380  00000007 ASL  00000061)
[    0.000000] ACPI: DSDT 00000000fffcbc59 03112 (v01   DELL    dt_ex 00001000 INTL 20050309)
[    0.000000] ACPI: FACS 00000000dfe8ac00 00040
[    0.000000] ACPI: SSDT 00000000fffcee8c 000AC (v01   DELL    st_ex 00001000 INTL 20050309)
[    0.000000] ACPI: APIC 00000000000fd44a 00072 (v01 DELL    WS 380  00000007 ASL  00000061)
[    0.000000] ACPI: BOOT 00000000000fd4bc 00028 (v01 DELL    WS 380  00000007 ASL  00000061)
[    0.000000] ACPI: ASF! 00000000000fd4e4 00067 (v16 DELL    WS 380  00000007 ASL  00000061)
[    0.000000] ACPI: MCFG 00000000000fd54b 0003E (v01 DELL    WS 380  00000007 ASL  00000061)
[    0.000000] ACPI: HPET 00000000000fd589 00038 (v01 DELL    WS 380  00000007 ASL  00000061)
[    0.000000] ACPI: SSDT 00000000dfe8ac40 00175 (v01 DpgPmm  Cpu0Ist 00000011 INTL 20050309)
[    0.000000] ACPI: SSDT 00000000dfe8b049 00175 (v01 DpgPmm  Cpu1Ist 00000011 INTL 20050309)
[    0.000000] ACPI: SSDT 00000000dfe8b452 00140 (v01 DpgPmm    CpuPm 00000010 INTL 20050309)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000021c000000
[    0.000000] Initmem setup node 0 0000000000000000-000000021c000000
[    0.000000]   NODE_DATA [000000021bffb000 - 000000021bffffff]
[    0.000000]  [ffffea0000000000-ffffea00087fffff] PMD -> [ffff880213600000-ffff88021b5fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x0021c000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x000000a0
[    0.000000]     0: 0x00000100 -> 0x000dfe8a
[    0.000000]     0: 0x00100000 -> 0x0021c000
[    0.000000] On node 0 totalpages: 2080282
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 12 pages reserved
[    0.000000]   DMA zone: 3908 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 16320 pages used for memmap
[    0.000000]   DMA32 zone: 896714 pages, LIFO batch:31
[    0.000000]   Normal zone: 18176 pages used for memmap
[    0.000000]   Normal zone: 1145088 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x05] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x07] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high level lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x08] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 8, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000dfe8a000 - 00000000dfe8b000
[    0.000000] PM: Registered nosave memory: 00000000dfe8b000 - 00000000dfe8c000
[    0.000000] PM: Registered nosave memory: 00000000dfe8c000 - 00000000dfe8d000
[    0.000000] PM: Registered nosave memory: 00000000dfe8d000 - 00000000dfe8e000
[    0.000000] PM: Registered nosave memory: 00000000dfe8e000 - 00000000dfe8f000
[    0.000000] PM: Registered nosave memory: 00000000dfe8f000 - 00000000e4000000
[    0.000000] PM: Registered nosave memory: 00000000e4000000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fed00000
[    0.000000] PM: Registered nosave memory: 00000000fed00000 - 00000000fed20000
[    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000feda0000
[    0.000000] PM: Registered nosave memory: 00000000feda0000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fef00000
[    0.000000] PM: Registered nosave memory: 00000000fef00000 - 00000000ffb00000
[    0.000000] PM: Registered nosave memory: 00000000ffb00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at e4000000 (gap: e4000000:1ac00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88021bc00000 s83136 r8192 d23360 u524288
[    0.000000] pcpu-alloc: s83136 r8192 d23360 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2045710
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-58-generic root=UUID=aa67efab-a30a-45f0-d228-60a73bc64935 ro
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 8093172k/8847360k available (6588k kernel code, 526232k absent, 227956k reserved, 6617k data, 924k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:16640 nr_irqs:712 16
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 67108864 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 3391.752 MHz processor.
[    0.004005] Calibrating delay loop (skipped), value calculated using timer frequency.. 6783.50 BogoMIPS (lpj=13567008)
[    0.004016] pid_max: default: 32768 minimum: 301
[    0.004050] Security Framework initialized
[    0.004072] AppArmor: AppArmor initialized
[    0.004077] Yama: becoming mindful.
[    0.005177] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.012522] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.014839] Mount-cache hash table entries: 256
[    0.015047] Initializing cgroup subsys cpuacct
[    0.015057] Initializing cgroup subsys memory
[    0.015070] Initializing cgroup subsys devices
[    0.015075] Initializing cgroup subsys freezer
[    0.015080] Initializing cgroup subsys blkio
[    0.015092] Initializing cgroup subsys perf_event
[    0.015142] CPU: Physical Processor ID: 0
[    0.015148] CPU: Processor Core ID: 0
[    0.015152] mce: CPU supports 4 MCE banks
[    0.015168] CPU0: Thermal monitoring enabled (TM1)
[    0.015177] using mwait in idle threads.
[    0.017707] ACPI: Core revision 20110623
[    0.090110] ftrace: allocating 26602 entries in 105 pages
[    0.092449] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.132575] CPU0: Intel(R) Pentium(R) D CPU 3.40GHz stepping 04
[    0.136007] Performance Events: Netburst events, Netburst P4/Xeon PMU driver.
[    0.136007] ... version:                0
[    0.136007] ... bit width:              40
[    0.136007] ... generic registers:      18
[    0.136007] ... value mask:             000000ffffffffff
[    0.136007] ... max period:             0000007fffffffff
[    0.136007] ... fixed-purpose events:   0
[    0.136007] ... event mask:             000000000003ffff
[    0.136007] NMI watchdog enabled, takes one hw-pmu counter.
[    0.136007] Booting Node   0, Processors  #1
[    0.136007] smpboot cpu 1: start_ip = 94000
[    0.224040] NMI watchdog enabled, takes one hw-pmu counter.
[    0.224087] Brought up 2 CPUs
[    0.224094] Total of 2 processors activated (13566.71 BogoMIPS).
[    0.225811] devtmpfs: initialized
[    0.225811] EVM: security.selinux
[    0.225811] EVM: security.SMACK64
[    0.225811] EVM: security.capability
[    0.225811] PM: Registering ACPI NVS region at dfe8ac00 (8192 bytes)
[    0.228856] print_constraints: dummy: 
[    0.228893] RTC time:  2:10:53, date: 01/15/14
[    0.228943] NET: Registered protocol family 16
[    0.229056] Trying to unpack rootfs image as initramfs...
[    0.236488] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.236498] ACPI: bus type pci registered
[    0.236583] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xe0000000-0xe3ffffff] (base 0xe0000000)
[    0.236592] PCI: MMCONFIG at [mem 0xe0000000-0xe3ffffff] reserved in E820
[    0.257279] PCI: Using configuration type 1 for base access
[    0.268510] bio: create slab <bio-0> at 0
[    0.268658] ACPI: Added _OSI(Module Device)
[    0.268664] ACPI: Added _OSI(Processor Device)
[    0.268668] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.268672] ACPI: Added _OSI(Processor Aggregator Device)
[    0.269491] ACPI: EC: Look up EC in DSDT
[    0.303227] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.320786] ACPI: Interpreter enabled
[    0.320799] ACPI: (supports S0 S1 S3 S4 S5)
[    0.320833] ACPI: Using IOAPIC for interrupt routing
[    0.438937] ACPI: No dock devices found.
[    0.438948] HEST: Table not found.
[    0.438954] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.472197] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.512143] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.512149] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.512152] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.512155] pci_root PNP0A03:00: host bridge window [mem 0x000c0000-0x000effff] (ignored)
[    0.512159] pci_root PNP0A03:00: host bridge window [mem 0x000f0000-0x000fffff] (ignored)
[    0.512162] pci_root PNP0A03:00: host bridge window [mem 0xdff00000-0xdfffffff] (ignored)
[    0.512165] pci_root PNP0A03:00: host bridge window [mem 0xe4000000-0xfebfffff] (ignored)
[    0.512168] pci_root PNP0A03:00: host bridge window [mem 0xffa80800-0xffa80bff] (ignored)
[    0.512171] pci_root PNP0A03:00: host bridge window [mem 0xffa7c000-0xffa7ffff] (ignored)
[    0.512189] pci 0000:00:00.0: [8086:2774] type 0 class 0x000600
[    0.512249] pci 0000:00:01.0: [8086:2775] type 1 class 0x000604
[    0.512302] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.512306] pci 0000:00:01.0: PME# disabled
[    0.512363] pci 0000:00:1b.0: [8086:27d8] type 0 class 0x000403
[    0.512382] pci 0000:00:1b.0: reg 10: [mem 0xfebfc000-0xfebfffff 64bit]
[    0.512458] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.512462] pci 0000:00:1b.0: PME# disabled
[    0.512486] pci 0000:00:1c.0: [8086:27d0] type 1 class 0x000604
[    0.512565] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.512569] pci 0000:00:1c.0: PME# disabled
[    0.512598] pci 0000:00:1c.4: [8086:27e0] type 1 class 0x000604
[    0.512675] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.512680] pci 0000:00:1c.4: PME# disabled
[    0.512705] pci 0000:00:1c.5: [8086:27e2] type 1 class 0x000604
[    0.512783] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.512787] pci 0000:00:1c.5: PME# disabled
[    0.512811] pci 0000:00:1d.0: [8086:27c8] type 0 class 0x000c03
[    0.512856] pci 0000:00:1d.0: reg 20: [io  0xff80-0xff9f]
[    0.512891] pci 0000:00:1d.1: [8086:27c9] type 0 class 0x000c03
[    0.512936] pci 0000:00:1d.1: reg 20: [io  0xff60-0xff7f]
[    0.512971] pci 0000:00:1d.2: [8086:27ca] type 0 class 0x000c03
[    0.513015] pci 0000:00:1d.2: reg 20: [io  0xff40-0xff5f]
[    0.513050] pci 0000:00:1d.3: [8086:27cb] type 0 class 0x000c03
[    0.513094] pci 0000:00:1d.3: reg 20: [io  0xff20-0xff3f]
[    0.513142] pci 0000:00:1d.7: [8086:27cc] type 0 class 0x000c03
[    0.513164] pci 0000:00:1d.7: reg 10: [mem 0xffa80800-0xffa80bff]
[    0.513253] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.513258] pci 0000:00:1d.7: PME# disabled
[    0.513279] pci 0000:00:1e.0: [8086:244e] type 1 class 0x000604
[    0.513350] pci 0000:00:1f.0: [8086:27b8] type 0 class 0x000601
[    0.513438] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0c00 (mask 007f)
[    0.513449] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at 00e0 (mask 0007)
[    0.513499] pci 0000:00:1f.1: [8086:27df] type 0 class 0x000101
[    0.513514] pci 0000:00:1f.1: reg 10: [io  0x01f0-0x01f7]
[    0.513524] pci 0000:00:1f.1: reg 14: [io  0x03f4-0x03f7]
[    0.513535] pci 0000:00:1f.1: reg 18: [io  0x0170-0x0177]
[    0.513545] pci 0000:00:1f.1: reg 1c: [io  0x0374-0x0377]
[    0.513555] pci 0000:00:1f.1: reg 20: [io  0xffa0-0xffaf]
[    0.513597] pci 0000:00:1f.2: [8086:27c3] type 0 class 0x000104
[    0.513615] pci 0000:00:1f.2: reg 10: [io  0xfe00-0xfe07]
[    0.513624] pci 0000:00:1f.2: reg 14: [io  0xfe10-0xfe13]
[    0.513633] pci 0000:00:1f.2: reg 18: [io  0xfe20-0xfe27]
[    0.513643] pci 0000:00:1f.2: reg 1c: [io  0xfe30-0xfe33]
[    0.513652] pci 0000:00:1f.2: reg 20: [io  0xfea0-0xfeaf]
[    0.513661] pci 0000:00:1f.2: reg 24: [mem 0xfebfbc00-0xfebfbfff]
[    0.513702] pci 0000:00:1f.2: PME# supported from D3hot
[    0.513706] pci 0000:00:1f.2: PME# disabled
[    0.513724] pci 0000:00:1f.3: [8086:27da] type 0 class 0x000c05
[    0.513779] pci 0000:00:1f.3: reg 20: [io  0xece0-0xecff]
[    0.513863] pci 0000:01:00.0: [10de:0f01] type 0 class 0x000300
[    0.513875] pci 0000:01:00.0: reg 10: [mem 0xfd000000-0xfdffffff]
[    0.513888] pci 0000:01:00.0: reg 14: [mem 0xf0000000-0xf7ffffff 64bit pref]
[    0.513901] pci 0000:01:00.0: reg 1c: [mem 0xf8000000-0xf9ffffff 64bit pref]
[    0.513910] pci 0000:01:00.0: reg 24: [io  0xdc80-0xdcff]
[    0.513919] pci 0000:01:00.0: reg 30: [mem 0xfea00000-0xfea7ffff pref]
[    0.513986] pci 0000:01:00.1: [10de:0bea] type 0 class 0x000403
[    0.513998] pci 0000:01:00.1: reg 10: [mem 0xfe9fc000-0xfe9fffff]
[    0.520070] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.520079] pci 0000:00:01.0:   bridge window [io  0xd000-0xdfff]
[    0.520084] pci 0000:00:01.0:   bridge window [mem 0xfd000000-0xfeafffff]
[    0.520089] pci 0000:00:01.0:   bridge window [mem 0xf0000000-0xf9ffffff 64bit pref]
[    0.520136] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.520145] pci 0000:00:1c.0:   bridge window [mem 0xfcf00000-0xfcffffff]
[    0.520194] pci 0000:00:1c.4: PCI bridge to [bus 03-03]
[    0.520273] pci 0000:04:00.0: [14e4:1677] type 0 class 0x000200
[    0.520300] pci 0000:04:00.0: reg 10: [mem 0xfcef0000-0xfcefffff 64bit]
[    0.520431] pci 0000:04:00.0: PME# supported from D3hot D3cold
[    0.520437] pci 0000:04:00.0: PME# disabled
[    0.528110] pci 0000:00:1c.5: PCI bridge to [bus 04-04]
[    0.528122] pci 0000:00:1c.5:   bridge window [mem 0xfce00000-0xfcefffff]
[    0.528171] pci 0000:05:02.0: [11c1:5811] type 0 class 0x000c00
[    0.528191] pci 0000:05:02.0: reg 10: [mem 0xfcdff000-0xfcdfffff]
[    0.528274] pci 0000:05:02.0: supports D1 D2
[    0.528276] pci 0000:05:02.0: PME# supported from D0 D1 D2 D3hot
[    0.528281] pci 0000:05:02.0: PME# disabled
[    0.528329] pci 0000:00:1e.0: PCI bridge to [bus 05-05] (subtractive decode)
[    0.528339] pci 0000:00:1e.0:   bridge window [mem 0xfcd00000-0xfcdfffff]
[    0.528347] pci 0000:00:1e.0:   bridge window [io  0x0000-0xffff] (subtractive decode)
[    0.528350] pci 0000:00:1e.0:   bridge window [mem 0x00000000-0xfffffffff] (subtractive decode)
[    0.528382] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.528749] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI4._PRT]
[    0.529107] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI2._PRT]
[    0.529357] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[    0.529562] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI5._PRT]
[    0.529788] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI6._PRT]
[    0.529966]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.529974]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    0.529980] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.871795] Freeing initrd memory: 14500k freed
[    1.264372] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 15)
[    1.264779] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[    1.265200] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 9 10 11 12 15)
[    1.265619] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[    1.266023] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 6 7 9 10 11 12 15)
[    1.266465] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *9 10 11 12 15)
[    1.266872] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 6 7 9 10 11 12 15)
[    1.267282] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[    1.267525] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    1.267525] vgaarb: loaded
[    1.267525] vgaarb: bridge control possible 0000:01:00.0
[    1.267525] i2c-core: driver [aat2870] using legacy suspend method
[    1.267525] i2c-core: driver [aat2870] using legacy resume method
[    1.267525] SCSI subsystem initialized
[    1.267525] libata version 3.00 loaded.
[    1.267525] usbcore: registered new interface driver usbfs
[    1.267525] usbcore: registered new interface driver hub
[    1.268088] usbcore: registered new device driver usb
[    1.268203] PCI: Using ACPI for IRQ routing
[    1.269737] PCI: pci_cache_line_size set to 64 bytes
[    1.269828] reserve RAM buffer: 00000000dfe8ac00 - 00000000dfffffff 
[    1.269968] NetLabel: Initializing
[    1.269973] NetLabel:  domain hash size = 128
[    1.269976] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.269993] NetLabel:  unlabeled traffic allowed by default
[    1.270034] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    1.270034] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    1.270034] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    1.278544] Switching to clocksource hpet
[    1.286359] AppArmor: AppArmor Filesystem Enabled
[    1.286407] pnp: PnP ACPI init
[    1.286432] ACPI: bus type pnp registered
[    1.291862] pnp 00:00: [bus 00-ff]
[    1.291867] pnp 00:00: [io  0x0cf8-0x0cff]
[    1.291870] pnp 00:00: [io  0x0000-0x0cf7 window]
[    1.291873] pnp 00:00: [io  0x0d00-0xffff window]
[    1.291876] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    1.291879] pnp 00:00: [mem 0x000c0000-0x000effff window]
[    1.291882] pnp 00:00: [mem 0x000f0000-0x000fffff window]
[    1.291885] pnp 00:00: [mem 0xdff00000-0xdfffffff window]
[    1.291888] pnp 00:00: [mem 0xe4000000-0xfebfffff window]
[    1.291891] pnp 00:00: [mem 0xffa80800-0xffa80bff window]
[    1.291893] pnp 00:00: [mem 0xffa7c000-0xffa7ffff window]
[    1.291952] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
[    1.294408] pnp 00:01: [io  0x0060]
[    1.294411] pnp 00:01: [io  0x0064]
[    1.294413] pnp 00:01: [io  0x0062-0x0063]
[    1.294416] pnp 00:01: [io  0x0065-0x006f]
[    1.294418] pnp 00:01: [io  0x00e0-0x00ef]
[    1.294420] pnp 00:01: [io  0x0800-0x085f]
[    1.294423] pnp 00:01: [io  0x0c00-0x0c7f]
[    1.294425] pnp 00:01: [io  0x0860-0x08ff]
[    1.294501] system 00:01: [io  0x0800-0x085f] has been reserved
[    1.294508] system 00:01: [io  0x0c00-0x0c7f] has been reserved
[    1.294513] system 00:01: [io  0x0860-0x08ff] has been reserved
[    1.294520] system 00:01: Plug and Play ACPI device, IDs PNP0c01 (active)
[    1.294728] pnp 00:02: [io  0x0080-0x009f]
[    1.294731] pnp 00:02: [io  0x0000-0x001f]
[    1.294734] pnp 00:02: [io  0x00c0-0x00df]
[    1.294737] pnp 00:02: [dma 4]
[    1.294771] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    1.294917] pnp 00:03: [io  0x00f0-0x00ff]
[    1.294933] pnp 00:03: [irq 13]
[    1.294971] pnp 00:03: Plug and Play ACPI device, IDs PNP0c04 (active)
[    1.295108] pnp 00:04: [io  0x0061]
[    1.295148] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
[    1.295305] pnp 00:05: [io  0x0070-0x007f]
[    1.295312] pnp 00:05: [irq 8]
[    1.295349] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
[    1.298860] pnp 00:06: [io  0x03f0-0x03f5]
[    1.298867] pnp 00:06: [io  0x03f7]
[    1.298873] pnp 00:06: [irq 6]
[    1.298876] pnp 00:06: [dma 2]
[    1.299299] pnp 00:06: Plug and Play ACPI device, IDs PNP0700 (active)
[    1.306206] pnp 00:07: [io  0x0378-0x037f]
[    1.306210] pnp 00:07: [io  0x0778-0x077f]
[    1.306216] pnp 00:07: [irq 7]
[    1.306219] pnp 00:07: [dma 0 disabled]
[    1.307269] pnp 00:07: Plug and Play ACPI device, IDs PNP0401 (active)
[    1.310011] pnp 00:08: [io  0x03f8-0x03ff]
[    1.310019] pnp 00:08: [irq 4]
[    1.310349] pnp 00:08: Plug and Play ACPI device, IDs PNP0501 (active)
[    1.324046] pnp 00:09: [mem 0x00000000-0x0009ffff]
[    1.324052] pnp 00:09: [mem 0x00100000-0x00ffffff]
[    1.324056] pnp 00:09: [mem 0x01000000-0xdfe8abff]
[    1.324059] pnp 00:09: [mem 0x000f0000-0x000fffff]
[    1.324063] pnp 00:09: [mem 0x000c0000-0x000d7fff]
[    1.324071] pnp 00:09: [mem 0xfec00000-0xfecfffff]
[    1.324073] pnp 00:09: [mem 0xfee00000-0xfeefffff]
[    1.324075] pnp 00:09: [mem 0xfed20000-0xfed9ffff]
[    1.324078] pnp 00:09: [mem 0xffb00000-0xffbfffff]
[    1.324080] pnp 00:09: [mem 0xffc00000-0xffffffff]
[    1.324156] system 00:09: [mem 0x00000000-0x0009ffff] could not be reserved
[    1.324164] system 00:09: [mem 0x00100000-0x00ffffff] could not be reserved
[    1.324170] system 00:09: [mem 0x01000000-0xdfe8abff] could not be reserved
[    1.324175] system 00:09: [mem 0x000f0000-0x000fffff] could not be reserved
[    1.324181] system 00:09: [mem 0x000c0000-0x000d7fff] could not be reserved
[    1.324186] system 00:09: [mem 0xfec00000-0xfecfffff] could not be reserved
[    1.324191] system 00:09: [mem 0xfee00000-0xfeefffff] has been reserved
[    1.324197] system 00:09: [mem 0xfed20000-0xfed9ffff] has been reserved
[    1.324202] system 00:09: [mem 0xffb00000-0xffbfffff] has been reserved
[    1.324207] system 00:09: [mem 0xffc00000-0xffffffff] has been reserved
[    1.324213] system 00:09: Plug and Play ACPI device, IDs PNP0c01 (active)
[    1.324618] pnp 00:0a: [mem 0xe0000000-0xe3ffffff]
[    1.324621] pnp 00:0a: [mem 0xfeda0000-0xfedacfff]
[    1.324689] system 00:0a: [mem 0xe0000000-0xe3ffffff] has been reserved
[    1.324695] system 00:0a: [mem 0xfeda0000-0xfedacfff] has been reserved
[    1.324702] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.324709] pnp: PnP ACPI: found 11 devices
[    1.324714] ACPI: ACPI bus type pnp unregistered
[    1.333887] PCI: max bus depth: 1 pci_try_num: 2
[    1.333933] pci 0000:00:1c.5: BAR 15: assigned [mem 0xe4000000-0xe41fffff 64bit pref]
[    1.333942] pci 0000:00:1c.5: BAR 13: assigned [io  0x1000-0x1fff]
[    1.333948] pci 0000:00:1c.4: BAR 14: assigned [mem 0xe4200000-0xe43fffff]
[    1.333954] pci 0000:00:1c.4: BAR 15: assigned [mem 0xe4400000-0xe45fffff 64bit pref]
[    1.333960] pci 0000:00:1c.4: BAR 13: assigned [io  0x2000-0x2fff]
[    1.333966] pci 0000:00:1c.0: BAR 15: assigned [mem 0xe4600000-0xe47fffff 64bit pref]
[    1.333973] pci 0000:00:1c.0: BAR 13: assigned [io  0x3000-0x3fff]
[    1.333980] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    1.333987] pci 0000:00:01.0:   bridge window [io  0xd000-0xdfff]
[    1.333993] pci 0000:00:01.0:   bridge window [mem 0xfd000000-0xfeafffff]
[    1.333999] pci 0000:00:01.0:   bridge window [mem 0xf0000000-0xf9ffffff 64bit pref]
[    1.334008] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    1.334013] pci 0000:00:1c.0:   bridge window [io  0x3000-0x3fff]
[    1.334020] pci 0000:00:1c.0:   bridge window [mem 0xfcf00000-0xfcffffff]
[    1.334027] pci 0000:00:1c.0:   bridge window [mem 0xe4600000-0xe47fffff 64bit pref]
[    1.334037] pci 0000:00:1c.4: PCI bridge to [bus 03-03]
[    1.334042] pci 0000:00:1c.4:   bridge window [io  0x2000-0x2fff]
[    1.334049] pci 0000:00:1c.4:   bridge window [mem 0xe4200000-0xe43fffff]
[    1.334056] pci 0000:00:1c.4:   bridge window [mem 0xe4400000-0xe45fffff 64bit pref]
[    1.334066] pci 0000:00:1c.5: PCI bridge to [bus 04-04]
[    1.334071] pci 0000:00:1c.5:   bridge window [io  0x1000-0x1fff]
[    1.334078] pci 0000:00:1c.5:   bridge window [mem 0xfce00000-0xfcefffff]
[    1.334085] pci 0000:00:1c.5:   bridge window [mem 0xe4000000-0xe41fffff 64bit pref]
[    1.334095] pci 0000:00:1e.0: PCI bridge to [bus 05-05]
[    1.334102] pci 0000:00:1e.0:   bridge window [mem 0xfcd00000-0xfcdfffff]
[    1.334128] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.334136] pci 0000:00:01.0: setting latency timer to 64
[    1.334144] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.334151] pci 0000:00:1c.0: setting latency timer to 64
[    1.334158] pci 0000:00:1c.4: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.334165] pci 0000:00:1c.4: setting latency timer to 64
[    1.334182] pci 0000:00:1c.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.334190] pci 0000:00:1c.5: setting latency timer to 64
[    1.334197] pci 0000:00:1e.0: setting latency timer to 64
[    1.334202] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
[    1.334205] pci_bus 0000:00: resource 1 [mem 0x00000000-0xfffffffff]
[    1.334208] pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]
[    1.334211] pci_bus 0000:01: resource 1 [mem 0xfd000000-0xfeafffff]
[    1.334214] pci_bus 0000:01: resource 2 [mem 0xf0000000-0xf9ffffff 64bit pref]
[    1.334217] pci_bus 0000:02: resource 0 [io  0x3000-0x3fff]
[    1.334220] pci_bus 0000:02: resource 1 [mem 0xfcf00000-0xfcffffff]
[    1.334222] pci_bus 0000:02: resource 2 [mem 0xe4600000-0xe47fffff 64bit pref]
[    1.334225] pci_bus 0000:03: resource 0 [io  0x2000-0x2fff]
[    1.334228] pci_bus 0000:03: resource 1 [mem 0xe4200000-0xe43fffff]
[    1.334231] pci_bus 0000:03: resource 2 [mem 0xe4400000-0xe45fffff 64bit pref]
[    1.334234] pci_bus 0000:04: resource 0 [io  0x1000-0x1fff]
[    1.334236] pci_bus 0000:04: resource 1 [mem 0xfce00000-0xfcefffff]
[    1.334239] pci_bus 0000:04: resource 2 [mem 0xe4000000-0xe41fffff 64bit pref]
[    1.334242] pci_bus 0000:05: resource 1 [mem 0xfcd00000-0xfcdfffff]
[    1.334245] pci_bus 0000:05: resource 4 [io  0x0000-0xffff]
[    1.334247] pci_bus 0000:05: resource 5 [mem 0x00000000-0xfffffffff]
[    1.334295] NET: Registered protocol family 2
[    1.334613] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    1.336655] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    1.341205] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    1.341775] TCP: Hash tables configured (established 524288 bind 65536)
[    1.341780] TCP reno registered
[    1.341802] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    1.341895] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    1.342082] NET: Registered protocol family 1
[    1.342139] pci 0000:00:1d.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    1.342161] pci 0000:00:1d.0: PCI INT A disabled
[    1.342177] pci 0000:00:1d.1: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[    1.342198] pci 0000:00:1d.1: PCI INT B disabled
[    1.342214] pci 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.342235] pci 0000:00:1d.2: PCI INT C disabled
[    1.342257] pci 0000:00:1d.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    1.342278] pci 0000:00:1d.3: PCI INT D disabled
[    1.342290] pci 0000:00:1d.7: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    1.342326] pci 0000:00:1d.7: PCI INT A disabled
[    1.342361] pci 0000:01:00.0: Boot video device
[    1.342381] PCI: CLS 64 bytes, default 64
[    1.342384] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    1.342390] Placing 64MB software IO TLB between ffff8800dbe84000 - ffff8800dfe84000
[    1.342396] software IO TLB at phys 0xdbe84000 - 0xdfe84000
[    1.342412] Simple Boot Flag at 0x7a set to 0x1
[    1.342892] audit: initializing netlink socket (disabled)
[    1.342906] type=2000 audit(1389751853.336:1): initialized
[    1.366203] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.369933] VFS: Disk quotas dquot_6.5.2
[    1.370009] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.370708] fuse init (API version 7.17)
[    1.370863] msgmni has been set to 15835
[    1.371538] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    1.371597] io scheduler noop registered
[    1.371602] io scheduler deadline registered
[    1.371651] io scheduler cfq registered (default)
[    1.371795] pcieport 0000:00:01.0: setting latency timer to 64
[    1.371836] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    1.371895] pcieport 0000:00:1c.0: setting latency timer to 64
[    1.371937] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
[    1.372009] pcieport 0000:00:1c.4: setting latency timer to 64
[    1.372067] pcieport 0000:00:1c.4: irq 42 for MSI/MSI-X
[    1.372135] pcieport 0000:00:1c.5: setting latency timer to 64
[    1.372177] pcieport 0000:00:1c.5: irq 43 for MSI/MSI-X
[    1.372286] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.372321] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.372486] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    1.372498] ACPI: Power Button [VBTN]
[    1.372565] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    1.372574] ACPI: Power Button [PWRF]
[    1.419778] ERST: Table is not found!
[    1.419783] GHES: HEST is not enabled!
[    1.419900] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.440332] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.568650] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.568981] Linux agpgart interface v0.103
[    1.571417] brd: module loaded
[    1.572673] loop: module loaded
[    1.572876] ahci 0000:00:1f.2: version 3.0
[    1.572899] ahci 0000:00:1f.2: PCI INT C -> GSI 20 (level, low) -> IRQ 20
[    1.572964] ahci 0000:00:1f.2: irq 44 for MSI/MSI-X
[    1.573035] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl RAID mode
[    1.573043] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part 
[    1.573050] ahci 0000:00:1f.2: setting latency timer to 64
[    1.573825] scsi0 : ahci
[    1.573945] scsi1 : ahci
[    1.574083] scsi2 : ahci
[    1.574198] scsi3 : ahci
[    1.574269] ata1: SATA max UDMA/133 abar m1024@0xfebfbc00 port 0xfebfbd00 irq 44
[    1.574276] ata2: SATA max UDMA/133 abar m1024@0xfebfbc00 port 0xfebfbd80 irq 44
[    1.574282] ata3: SATA max UDMA/133 abar m1024@0xfebfbc00 port 0xfebfbe00 irq 44
[    1.574288] ata4: SATA max UDMA/133 abar m1024@0xfebfbc00 port 0xfebfbe80 irq 44
[    1.574407] ata_piix 0000:00:1f.1: version 2.13
[    1.574418] ata_piix 0000:00:1f.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.574483] ata_piix 0000:00:1f.1: setting latency timer to 64
[    1.574907] scsi4 : ata_piix
[    1.575016] scsi5 : ata_piix
[    1.575078] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    1.575084] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    1.575320] ata6: port disabled--ignoring
[    1.575596] Fixed MDIO Bus: probed
[    1.575629] tun: Universal TUN/TAP device driver, 1.6
[    1.575634] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.575722] PPP generic driver version 2.4.2
[    1.575910] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.575939] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    1.575968] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.575974] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.576070] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    1.576118] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    1.576132] ehci_hcd 0000:00:1d.7: debug port 1
[    1.580017] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    1.580040] ehci_hcd 0000:00:1d.7: irq 21, io mem 0xffa80800
[    1.592020] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.592243] hub 1-0:1.0: USB hub found
[    1.592252] hub 1-0:1.0: 8 ports detected
[    1.592365] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.592386] uhci_hcd: USB Universal Host Controller Interface driver
[    1.592410] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    1.592422] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.592426] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.592499] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.592528] uhci_hcd 0000:00:1d.0: irq 21, io base 0x0000ff80
[    1.592742] hub 2-0:1.0: USB hub found
[    1.592750] hub 2-0:1.0: 2 ports detected
[    1.592847] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[    1.592858] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.592862] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.592944] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    1.592986] uhci_hcd 0000:00:1d.1: irq 22, io base 0x0000ff60
[    1.593196] hub 3-0:1.0: USB hub found
[    1.593204] hub 3-0:1.0: 2 ports detected
[    1.593288] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.593302] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.593307] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.593384] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    1.593425] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000ff40
[    1.593633] hub 4-0:1.0: USB hub found
[    1.593641] hub 4-0:1.0: 2 ports detected
[    1.593726] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    1.593737] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    1.593741] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    1.593816] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    1.593854] uhci_hcd 0000:00:1d.3: irq 23, io base 0x0000ff20
[    1.594065] hub 5-0:1.0: USB hub found
[    1.594072] hub 5-0:1.0: 2 ports detected
[    1.594218] usbcore: registered new interface driver libusual
[    1.594271] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    1.597108] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.597119] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.597341] mousedev: PS/2 mouse device common for all mice
[    1.597593] rtc_cmos 00:05: RTC can wake from S4
[    1.597741] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.597776] rtc0: alarms up to one day, 242 bytes nvram, hpet irqs
[    1.597907] device-mapper: uevent: version 1.0.3
[    1.598021] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    1.598034] cpuidle: using governor ladder
[    1.598038] cpuidle: using governor menu
[    1.598042] EFI Variables Facility v0.08 2004-May-17
[    1.598363] TCP cubic registered
[    1.598501] NET: Registered protocol family 10
[    1.599119] NET: Registered protocol family 17
[    1.599130] Registering the dns_resolver key type
[    1.599350] PM: Hibernation image not present or could not be loaded.
[    1.599367] registered taskstats version 1
[    1.607855]   Magic number: 14:918:156
[    1.607885] bdi 1:8: hash matches
[    1.607964] rtc_cmos 00:05: setting system clock to 2014-01-15 02:10:54 UTC (1389751854)
[    1.608382] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.608388] EDD information not available.
[    1.892037] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.892071] ata2: SATA link down (SStatus 0 SControl 300)
[    1.892109] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.892136] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.893495] ata3.00: ATA-8: ST31000340AS, AD14, max UDMA/133
[    1.893506] ata3.00: 1953525168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    1.895387] ata3.00: configured for UDMA/133
[    1.920611] ata4.00: ATA-8: ST31000333AS, SD35, max UDMA/133
[    1.920619] ata4.00: 1953525168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    1.928320] ata5.00: ATAPI: TSSTcorp CDDVDW SH-S202N, SB02, max UDMA/66
[    1.928331] ata5.01: ATAPI: LITE-ON DVDRW LH-18A1P, GL0B, max UDMA/66
[    1.935275] ata1.00: ATA-7: ST3500630AS, 3.AAC, max UDMA/133
[    1.935286] ata1.00: 976773168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    1.944202] ata5.00: configured for UDMA/66
[    1.962266] ata4.00: configured for UDMA/133
[    1.976197] ata5.01: configured for UDMA/66
[    1.993582] ata1.00: configured for UDMA/133
[    1.993725] scsi 0:0:0:0: Direct-Access     ATA      ST3500630AS      3.AA PQ: 0 ANSI: 5
[    1.993929] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.993972] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.994007] sd 0:0:0:0: [sda] Write Protect is off
[    1.994019] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.994049] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.994225] scsi 2:0:0:0: Direct-Access     ATA      ST31000340AS     AD14 PQ: 0 ANSI: 5
[    1.994417] sd 2:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    1.994502] sd 2:0:0:0: [sdb] Write Protect is off
[    1.994508] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.994539] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.994771] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    1.994995] scsi 3:0:0:0: Direct-Access     ATA      ST31000333AS     SD35 PQ: 0 ANSI: 5
[    1.995164] sd 3:0:0:0: [sdc] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    1.995228] sd 3:0:0:0: Attached scsi generic sg2 type 0
[    1.995272] sd 3:0:0:0: [sdc] Write Protect is off
[    1.995279] sd 3:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    1.995411] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.996018] scsi 4:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-S202N  SB02 PQ: 0 ANSI: 5
[    1.998388] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.998399] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.998541] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    1.998613] sr 4:0:0:0: Attached scsi generic sg3 type 5
[    2.000187] scsi 4:0:1:0: CD-ROM            LITE-ON  DVDRW LH-18A1P   GL0B PQ: 0 ANSI: 5
[    2.002943] sr1: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.003077] sr 4:0:1:0: Attached scsi CD-ROM sr1
[    2.003143] sr 4:0:1:0: Attached scsi generic sg4 type 5
[    2.018164]  sdb: sdb1
[    2.018467] sd 2:0:0:0: [sdb] Attached SCSI disk
[    2.020932]  sdc: sdc1
[    2.021208] sd 3:0:0:0: [sdc] Attached SCSI disk
[    2.052088]  sda: sda1 sda2 < sda5 >
[    2.052453] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.054504] Freeing unused kernel memory: 924k freed
[    2.054892] Write protecting the kernel read-only data: 12288k
[    2.061653] Freeing unused kernel memory: 1584k freed
[    2.067330] Freeing unused kernel memory: 1188k freed
[    2.090802] udevd[96]: starting version 175
[    2.124539] xor: automatically using best checksumming function: generic_sse
[    2.144018]    generic_sse:  5134.000 MB/sec
[    2.144024] xor: using function: generic_sse (5134.000 MB/sec)
[    2.148420] device-mapper: dm-raid45: initialized v0.2594b
[    2.157014] md: linear personality registered for level -1
[    2.164124] md: multipath personality registered for level -4
[    2.173209] md: raid0 personality registered for level 0
[    2.181775] md: raid1 personality registered for level 1
[    2.186304] async_tx: api initialized (async)
[    2.226057] firewire_ohci 0000:05:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.252056] raid6: int64x1   1473 MB/s
[    2.256040] usb 3-2: new full-speed USB device number 2 using uhci_hcd
[    2.262463] tg3.c:v3.121 (November 2, 2011)
[    2.262487] tg3 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.262501] tg3 0000:04:00.0: setting latency timer to 64
[    2.280081] firewire_ohci: Added fw-ohci device 0000:05:02.0, OHCI v1.0, 8 IR + 8 IT contexts, quirks 0x0
[    2.306138] Floppy drive(s): fd0 is 1.44M
[    2.320011] raid6: int64x2   2084 MB/s
[    2.388011] raid6: int64x4   2171 MB/s
[    2.456037] raid6: int64x8   1828 MB/s
[    2.524029] raid6: sse2x1    2440 MB/s
[    2.592014] raid6: sse2x2    3467 MB/s
[    2.660013] raid6: sse2x4    3503 MB/s
[    2.660018] raid6: using algorithm sse2x4 (3503 MB/s)
[    2.660066] usb 5-2: new full-speed USB device number 2 using uhci_hcd
[    2.660119] Refined TSC clocksource calibration: 3391.587 MHz.
[    2.660134] Switching to clocksource tsc
[    2.660632] FDC 0 is a post-1991 82077
[    2.662299] md: raid6 personality registered for level 6
[    2.662306] md: raid5 personality registered for level 5
[    2.662310] md: raid4 personality registered for level 4
[    2.675607] md: raid10 personality registered for level 10
[    2.697923] tg3 0000:04:00.0: eth0: Tigon3 [partno(BCM5751PKFBG) rev 4001] (PCI Express) MAC address 00:13:72:2c:f9:89
[    2.697938] tg3 0000:04:00.0: eth0: attached PHY is 5750 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[0])
[    2.697945] tg3 0000:04:00.0: eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    2.697952] tg3 0000:04:00.0: eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    2.845345] usbcore: registered new interface driver usbhid
[    2.845360] usbhid: USB HID core driver
[    2.855331] logitech-djreceiver 0003:046D:C52B.0003: hiddev0,hidraw0: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.3-2/input2
[    2.860257] input: Logitech Unifying Device. Wireless PID:4008 as /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.2/0003:046D:C52B.0003/input/input2
[    2.860479] logitech-djdevice 0003:046D:C52B.0004: input,hidraw1: USB HID v1.11 Mouse [Logitech Unifying Device. Wireless PID:4008] on usb-0000:00:1d.3-2:1
[    2.862383] input: Logitech Unifying Device. Wireless PID:4003 as /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.2/0003:046D:C52B.0003/input/input3
[    2.862517] logitech-djdevice 0003:046D:C52B.0005: input,hidraw2: USB HID v1.11 Keyboard [Logitech Unifying Device. Wireless PID:4003] on usb-0000:00:1d.3-2:2
[    3.160189] firewire_core: created device fw0: GUID 0000d10080ce6a4f, S400
[   12.709403] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   27.287515] Adding 4064252k swap on /dev/sda5.  Priority:-1 extents:1 across:4064252k 
[   27.357299] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   27.539589] EXT4-fs (dm-1): mounted filesystem with ordered data mode. Opts: errors=remount-ro
[   28.294504] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   28.327803] RPC: Registered named UNIX socket transport module.
[   28.327808] RPC: Registered udp transport module.
[   28.327810] RPC: Registered tcp transport module.
[   28.327813] RPC: Registered tcp NFSv4.1 backchannel transport module.
[   28.330091] FS-Cache: Loaded
[   28.341268] FS-Cache: Netfs 'nfs' registered for caching
[   28.350161] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[   28.354713] udevd[755]: starting version 175
[   28.413373] lp: driver loaded but no devices found
[   28.455618] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   28.455683] snd_hda_intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[   28.455714] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[   28.490752] intel_rng: Firmware space is locked read-only. If you can't or
[   28.490755] intel_rng: don't want to disable this in firmware setup, and if
[   28.490756] intel_rng: you are certain that your system has a functional
[   28.490757] intel_rng: RNG, try using the 'no_fwh_detect' option.
[   28.505002] leds_ss4200: no LED devices found
[   28.513665] input: HDA Intel Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input4
[   28.514041] input: HDA Intel Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input5
[   28.514678] input: HDA Intel Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[   28.514851] input: HDA Intel Line-Out as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   28.515435] snd_hda_intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   28.515440] hda_intel: Disabling MSI
[   28.515514] snd_hda_intel 0000:01:00.1: setting latency timer to 64
[   28.522973] usbcore: registered new interface driver usbserial
[   28.522993] USB Serial support registered for generic
[   28.523038] usbcore: registered new interface driver usbserial_generic
[   28.523041] usbserial: USB Serial Driver core
[   28.523499] USB Serial support registered for pl2303
[   28.523518] pl2303 3-2:1.0: pl2303 converter detected
[   28.538246] usb 3-2: pl2303 converter now attached to ttyUSB0
[   28.538307] usbcore: registered new interface driver pl2303
[   28.538311] pl2303: Prolific PL2303 USB to serial adaptor driver
[   28.569183] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   28.603634] parport_pc 00:07: reported by Plug and Play ACPI
[   28.603693] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[   28.606618] device-mapper: multipath: version 1.3.1 loaded
[   28.700420] lp0: using parport0 (interrupt-driven).
[   28.753216] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   28.968358] ppdev: user-space parallel port driver
[   29.392098] HDMI status: Codec=0 Pin=5 Presence_Detect=0 ELD_Valid=0
[   29.417009] HDMI status: Codec=1 Pin=5 Presence_Detect=0 ELD_Valid=0
[   29.440115] HDMI status: Codec=2 Pin=5 Presence_Detect=0 ELD_Valid=0
[   29.464136] HDMI status: Codec=3 Pin=5 Presence_Detect=0 ELD_Valid=0
[   29.464273] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input8
[   29.464553] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input9
[   29.464723] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input10
[   29.464884] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input11
[   29.745307] init: failsafe main process (1018) killed by TERM signal
[   31.539030] tg3 0000:04:00.0: eth0: Link is up at 1000 Mbps, full duplex
[   31.539035] tg3 0000:04:00.0: eth0: Flow control is off for TX and off for RX
[   31.539939] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   33.888543] vesafb: mode is 640x480x32, linelength=2560, pages=0
[   33.888547] vesafb: scrolling: redraw
[   33.888551] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[   33.890204] vesafb: framebuffer at 0xf9000000, mapped to 0xffffc90005e00000, using 1216k, total 1216k
[   33.890977] Console: switching to colour frame buffer device 80x30
[   33.892105] fb0: VESA VGA frame buffer device
[   42.240028] eth0: no IPv6 routers present
[   45.098264] CIFS VFS: default security mechanism requested.  The default security mechanism will be upgraded from ntlm to ntlmv2 in kernel release 3.3
[  210.537194] init: tty1 main process ended, respawning
[  345.128570] init: tty1 main process ended, respawning

```

dmraid -n /dev/sdb

```
/dev/sdb: "isw" and "ddf1" formats discovered (using ddf1)!
/dev/sdb (ddf1):
DDF1 anchor at 1953525167 with tables in big-endian format.
DDF1 Header at 0x1cf8660
0x000 signature:	0xDE11DE11
0x004 crc:		0x8AE627E7
0x008 guid:		"MARVELL ..Ea..Ea....70]P" [4d 41 52 56 45 4c 4c 20 ab 11 45 61 ab 11 45 61 fc 05 9a 01 37 30 5d 50]
0x020 rev:		"01.02.00" [30 31 2e 30 32 2e 30 30]
0x028 seqnum:		-1
0x02c timestamp:	0x505D3037
0x030 open:		0xFF
0x031 foreign:		0x0
0x032 grouping:		0x0
0x060 primary header:	1953524913
0x068 secondary header:	1953459632
0x070 header type:	0x1
0x074 workspace len:	128
0x078 workspace lba:	1953525040
0x080 max pd:		63
0x082 max vd:		63
0x084 max part:		16
0x086 vd_config len:	3
0x088 max_primary_elts:	64
0x0c0 adapter_offset:	1
0x0c4 adapter_len:	1
0x0c8 pd_offset:	2
0x0cc pd_len:		8
0x0d0 vd_offset:	10
0x0d4 vd_len:		8
0x0d8 config_offset:	18
0x0dc config_len:	51
0x0e0 disk_data_offset:	69
0x0e4 disk_data_len:	1
0x0e8 badblock_offset:	70
0x0ec badblock_len:	8
0x0f0 diag_offset:	-1
0x0f4 diag_len:		-1
0x0f8 vendor_offset:	76
0x0fc vendor_len:	5
DDF1 Header at 0x1cf88d0
0x000 signature:	0xDE11DE11
0x004 crc:		0x58C3AD66
0x008 guid:		"MARVELL ..Ea..Ea.....5]P" [4d 41 52 56 45 4c 4c 20 ab 11 45 61 ab 11 45 61 f3 10 b0 01 db 35 5d 50]
0x020 rev:		"01.02.00" [30 31 2e 30 32 2e 30 30]
0x028 seqnum:		-1
0x02c timestamp:	0x505D35DB
0x030 open:		0xFF
0x031 foreign:		0x0
0x032 grouping:		0x0
0x060 primary header:	1953524913
0x068 secondary header:	1953459632
0x070 header type:	0x1
0x074 workspace len:	128
0x078 workspace lba:	1953525040
0x080 max pd:		63
0x082 max vd:		63
0x084 max part:		16
0x086 vd_config len:	3
0x088 max_primary_elts:	64
0x0c0 adapter_offset:	1
0x0c4 adapter_len:	1
0x0c8 pd_offset:	2
0x0cc pd_len:		8
0x0d0 vd_offset:	10
0x0d4 vd_len:		8
0x0d8 config_offset:	18
0x0dc config_len:	51
0x0e0 disk_data_offset:	69
0x0e4 disk_data_len:	1
0x0e8 badblock_offset:	70
0x0ec badblock_len:	8
0x0f0 diag_offset:	-1
0x0f4 diag_len:		-1
0x0f8 vendor_offset:	76
0x0fc vendor_len:	5
Adapter Data at 0x1cf8ae0
0x000 signature:	0xAD111111
0x004 crc:		0xBD7214E8
0x008 guid:		"MARVELL ..Ea..Ea.....5]P" [4d 41 52 56 45 4c 4c 20 ab 11 45 61 ab 11 45 61 f3 10 b0 01 db 35 5d 50]
0x020 pci vendor:	0x11AB
0x022 pci device:	0x6145
0x024 pci subvendor:	0x11AB
0x026 pci subdevice:	0x6145
Disk Data at 0x1cf8cf0
0x000 signature:	0x33333333
0x004 crc:		0x3DB66A86
0x008 guid:		"Z-.%...................." [5a 2d fe 25 ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff]
0x020 reference:		0x25FE2D5A
0x024 forced_ref_flag:	255
0x025 forced_guid_flag:	255
Physical Drive Header at 0x1cf8f00
0x000 signature:	0x22222222
0x004 crc:		0xC17E97A1
0x008 num drives:	2
0x00a max drives:	32
Physical Drive at 0x1cf8f40
0x000 guid:		".E-....................." [97 45 2d bf ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff]
0x018 reference #:	0xBF2D4597
0x01c type:		0x0
0x01e state:		0x1
0x020 size:		1953394096
0x028 path info:	".................." [ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff]
Physical Drive at 0x1cf8f80
0x000 guid:		"Z-.%...................." [5a 2d fe 25 ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff]
0x018 reference #:	0x25FE2D5A
0x01c type:		0x0
0x01e state:		0x1
0x020 size:		1953394096
0x028 path info:	".................." [ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff]
Virtual Drive Header at 0x1cf9f10
0x000 signature:	0xDDDDDDDD
0x004 crc:		0xFFD1B631
0x008 num drives:	1
0x00a max drives:	16
Virtual Drive at 0x1cf9f50
0x000 guid:		"FX..FX.................." [46 58 03 00 46 58 00 00 ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff]
0x018 vd #:		0x0
0x01c type:		0x0
0x020 state:		0x0
0x021 init state:	0x0
0x030 name:		"................" [00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00]
Virtual Drive Config Record at 0x1cfaf20
0x000 signature:	0xEEEEEEEE
0x004 crc:		0x2235AAD6
0x008 guid:		"FX..FX....Ea..Ea........" [46 58 03 00 46 58 00 00 ab 11 45 61 ab 11 45 61 ff ff ff ff ff ff ff ff]
0x020 timestamp:	0x505D35DB
0x024 seqnum:		2
0x040 primary count:	2
0x042 stripe size:	7KiB
0x043 raid level:	0
0x044 raid qualifier:	0
0x045 secondary count:	1
0x046 secondary number:	0
0x047 secondary level:	0
0x060 spare 0:		0xFFFFFFFF
0x064 spare 1:		0xFFFFFFFF
0x068 spare 2:		0xFFFFFFFF
0x06c spare 3:		0xFFFFFFFF
0x070 spare 4:		0xFFFFFFFF
0x074 spare 5:		0xFFFFFFFF
0x078 spare 6:		0xFFFFFFFF
0x07c spare 7:		0xFFFFFFFF
0x080 cache policy:	0xFFFFFFFF
0x088 bg task rate:	128
0x048 sector count:	1953394096
0x050 size:		3906787072
Drive map:
0: BF2D4597 @ 0
1: 25FE2D5A @ 0

```

dmraid -n /dev/sdb -f isw

```
/dev/sdb (isw):
0x000 sig: "  Intel Raid ISM Cfg Sig. 1.1.00"
0x020 check_sum: 1616155193
0x024 mpb_size: 480
0x028 family_num: 2615808582
0x02c generation_num: 29
0x030 error_log_size: 0
0x034 attributes: 3221225472
0x038 num_disks: 2
0x039 num_raid_devs: 1
0x03a error_log_pos: 0
0x03c cache_size: 0
0x040 orig_family_num: 0
0x044 power_cycle_count: 0
0x048 bbm_log_size: 0
0x0d8 disk[0].serial: "        3QJ00LH1"
0x0e8 disk[0].totalBlocks: 1953525168
0x0ec disk[0].scsiId: 0x20000
0x0f0 disk[0].status: 0x13a
0x0f4 disk[0].owner_cfg_num: 0x0
0x108 disk[1].serial: "        9TE09F83"
0x118 disk[1].totalBlocks: 1953525168
0x11c disk[1].scsiId: 0x10100
0x120 disk[1].status: 0x13a
0x124 disk[1].owner_cfg_num: 0x0
0x138 isw_dev[0].volume: "         Volume0"
0x14c isw_dev[0].SizeHigh: 0
0x148 isw_dev[0].SizeLow: 1953519616
0x150 isw_dev[0].status: 0xc
0x154 isw_dev[0].reserved_blocks: 0
0x158 isw_dev[0].migr_priority: 0
0x159 isw_dev[0].num_sub_vol: 0
0x15a isw_dev[0].tid: 0
0x15b isw_dev[0].cng_master_disk: 0
0x15c isw_dev[0].cache_policy: 0
0x15e isw_dev[0].cng_state: 0
0x15f isw_dev[0].cng_sub_state: 0
0x188 isw_dev[0].vol.curr_migr_unit: 0
0x18c isw_dev[0].vol.check_point_id: 0
0x190 isw_dev[0].vol.migr_state: 0
0x191 isw_dev[0].vol.migr_type: 0
0x192 isw_dev[0].vol.dirty: 0
0x193 isw_dev[0].vol.fs_state: 0
0x194 isw_dev[0].vol.verify_errors: 0
0x196 isw_dev[0].vol.verify_bad_blocks: 0
0x1a8 isw_dev[0].vol.map[0].pba_of_lba0: 0
0x1ac isw_dev[0].vol.map[0].blocks_per_member: 1953519616
0x1b0 isw_dev[0].vol.map[0].num_data_stripes: 7630936
0x1b4 isw_dev[0].vol.map[0].blocks_per_strip: 128
0x1b6 isw_dev[0].vol.map[0].map_state: 0
0x1b7 isw_dev[0].vol.map[0].raid_level: 1
0x1b8 isw_dev[0].vol.map[0].num_members: 2
0x1b9 isw_dev[0].vol.map[0].num_domains: 2
0x1ba isw_dev[0].vol.map[0].failed_disk_num: 255
0x1bb isw_dev[0].vol.map[0].ddf: 1
0x1d8 isw_dev[0].vol.map[0].disk_ord_tbl[0]: 0x0
0x1dc isw_dev[0].vol.map[0].disk_ord_tbl[1]: 0x1

```

dmraid -n /dev/sdc

```
/dev/sdc (isw):
0x000 sig: "  Intel Raid ISM Cfg Sig. 1.1.00"
0x020 check_sum: 1616155193
0x024 mpb_size: 480
0x028 family_num: 2615808582
0x02c generation_num: 29
0x030 error_log_size: 0
0x034 attributes: 3221225472
0x038 num_disks: 2
0x039 num_raid_devs: 1
0x03a error_log_pos: 0
0x03c cache_size: 0
0x040 orig_family_num: 0
0x044 power_cycle_count: 0
0x048 bbm_log_size: 0
0x0d8 disk[0].serial: "        3QJ00LH1"
0x0e8 disk[0].totalBlocks: 1953525168
0x0ec disk[0].scsiId: 0x100
0x0f0 disk[0].status: 0x13a
0x0f4 disk[0].owner_cfg_num: 0x0
0x108 disk[1].serial: "        9TE09F83"
0x118 disk[1].totalBlocks: 1953525168
0x11c disk[1].scsiId: 0x30000
0x120 disk[1].status: 0x13a
0x124 disk[1].owner_cfg_num: 0x0
0x138 isw_dev[0].volume: "         Volume0"
0x14c isw_dev[0].SizeHigh: 0
0x148 isw_dev[0].SizeLow: 1953519616
0x150 isw_dev[0].status: 0xc
0x154 isw_dev[0].reserved_blocks: 0
0x158 isw_dev[0].migr_priority: 0
0x159 isw_dev[0].num_sub_vol: 0
0x15a isw_dev[0].tid: 0
0x15b isw_dev[0].cng_master_disk: 0
0x15c isw_dev[0].cache_policy: 0
0x15e isw_dev[0].cng_state: 0
0x15f isw_dev[0].cng_sub_state: 0
0x188 isw_dev[0].vol.curr_migr_unit: 0
0x18c isw_dev[0].vol.check_point_id: 0
0x190 isw_dev[0].vol.migr_state: 0
0x191 isw_dev[0].vol.migr_type: 0
0x192 isw_dev[0].vol.dirty: 0
0x193 isw_dev[0].vol.fs_state: 0
0x194 isw_dev[0].vol.verify_errors: 0
0x196 isw_dev[0].vol.verify_bad_blocks: 0
0x1a8 isw_dev[0].vol.map[0].pba_of_lba0: 0
0x1ac isw_dev[0].vol.map[0].blocks_per_member: 1953519616
0x1b0 isw_dev[0].vol.map[0].num_data_stripes: 7630936
0x1b4 isw_dev[0].vol.map[0].blocks_per_strip: 128
0x1b6 isw_dev[0].vol.map[0].map_state: 0
0x1b7 isw_dev[0].vol.map[0].raid_level: 1
0x1b8 isw_dev[0].vol.map[0].num_members: 2
0x1b9 isw_dev[0].vol.map[0].num_domains: 2
0x1ba isw_dev[0].vol.map[0].failed_disk_num: 255
0x1bb isw_dev[0].vol.map[0].ddf: 1
0x1d8 isw_dev[0].vol.map[0].disk_ord_tbl[0]: 0x0
0x1dc isw_dev[0].vol.map[0].disk_ord_tbl[1]: 0x1

```

dmraid -n /dev/sdc -f isw

```
/dev/sdc (isw):
0x000 sig: "  Intel Raid ISM Cfg Sig. 1.1.00"
0x020 check_sum: 1616155193
0x024 mpb_size: 480
0x028 family_num: 2615808582
0x02c generation_num: 29
0x030 error_log_size: 0
0x034 attributes: 3221225472
0x038 num_disks: 2
0x039 num_raid_devs: 1
0x03a error_log_pos: 0
0x03c cache_size: 0
0x040 orig_family_num: 0
0x044 power_cycle_count: 0
0x048 bbm_log_size: 0
0x0d8 disk[0].serial: "        3QJ00LH1"
0x0e8 disk[0].totalBlocks: 1953525168
0x0ec disk[0].scsiId: 0x100
0x0f0 disk[0].status: 0x13a
0x0f4 disk[0].owner_cfg_num: 0x0
0x108 disk[1].serial: "        9TE09F83"
0x118 disk[1].totalBlocks: 1953525168
0x11c disk[1].scsiId: 0x30000
0x120 disk[1].status: 0x13a
0x124 disk[1].owner_cfg_num: 0x0
0x138 isw_dev[0].volume: "         Volume0"
0x14c isw_dev[0].SizeHigh: 0
0x148 isw_dev[0].SizeLow: 1953519616
0x150 isw_dev[0].status: 0xc
0x154 isw_dev[0].reserved_blocks: 0
0x158 isw_dev[0].migr_priority: 0
0x159 isw_dev[0].num_sub_vol: 0
0x15a isw_dev[0].tid: 0
0x15b isw_dev[0].cng_master_disk: 0
0x15c isw_dev[0].cache_policy: 0
0x15e isw_dev[0].cng_state: 0
0x15f isw_dev[0].cng_sub_state: 0
0x188 isw_dev[0].vol.curr_migr_unit: 0
0x18c isw_dev[0].vol.check_point_id: 0
0x190 isw_dev[0].vol.migr_state: 0
0x191 isw_dev[0].vol.migr_type: 0
0x192 isw_dev[0].vol.dirty: 0
0x193 isw_dev[0].vol.fs_state: 0
0x194 isw_dev[0].vol.verify_errors: 0
0x196 isw_dev[0].vol.verify_bad_blocks: 0
0x1a8 isw_dev[0].vol.map[0].pba_of_lba0: 0
0x1ac isw_dev[0].vol.map[0].blocks_per_member: 1953519616
0x1b0 isw_dev[0].vol.map[0].num_data_stripes: 7630936
0x1b4 isw_dev[0].vol.map[0].blocks_per_strip: 128
0x1b6 isw_dev[0].vol.map[0].map_state: 0
0x1b7 isw_dev[0].vol.map[0].raid_level: 1
0x1b8 isw_dev[0].vol.map[0].num_members: 2
0x1b9 isw_dev[0].vol.map[0].num_domains: 2
0x1ba isw_dev[0].vol.map[0].failed_disk_num: 255
0x1bb isw_dev[0].vol.map[0].ddf: 1
0x1d8 isw_dev[0].vol.map[0].disk_ord_tbl[0]: 0x0
0x1dc isw_dev[0].vol.map[0].disk_ord_tbl[1]: 0x1

```

---

### Post by markius on 2014-01-15
[COLOR="#FF0000"]**Be very careful with this post.  Here be dragons**[/COLOR]

So just a hunch, but the DDF1 metadata begins with a static identifier (0xde11de11).  If you dump out the block using DD, can you hex edit that DWORD and replace it with something else (EG 0x00000000) and then write the modified block back (take a backup first!).  That should be enough to kill the Dell RAID information.  You only need to do this on /dev/sdb

---

### Post by markius on 2014-01-15
You could also simply try 
dmraid -r -E -f ddf1 /dev/sdb

Maybe dmraid has been fixed in the last year though I doubt it!

---

### Post by jsylvia007 on 2014-01-15
> **markius said:**
> You could also simply try 
dmraid -r -E -f ddf1 /dev/sdb

Maybe dmraid has been fixed in the last year though I doubt it!

You're correct, it hasn't been fixed in 12.04...  That was the first thing I tried...

I assume the block I want to edit is the one listed as the DDF1 anchor point?

EDIT:

So, I did:

dd if=/dev/sdb of=/root/ddf1.metadata.backup.sdb skip=1953525167 bs=512 count=1

and

dd if=/dev/sdc of=/root/ddf1.metadata.backup.sdc skip=1953525167 bs=512 count=1

just to compare those two sectors...  on sdc, instead of de11de11, it says EFI PART....

Should these be the same??

---

### Post by markius on 2014-01-17
I would change the de11de11 to 00000000 on sdc only.  That should be enough to kill the ddf1 metadata

---

### Post by jsylvia007 on 2014-01-17
> **markius said:**
> I would change the de11de11 to 00000000 on sdc only.  That should be enough to kill the ddf1 metadata

Just to clarify, the bad drive is sdb...  so I did this on sdb...  same exact issue.  The entire partition is corrupted with "cant find ext4 superblock".  I've tried running fsck to see, but it fails as well.

Then I have to dd back the original sector.

Any other thoughts?

---

### Post by markius on 2014-01-22
Did you say this was a RAID1 mirror?

---

### Post by jsylvia007 on 2014-01-22
> **markius said:**
> Did you say this was a RAID1 mirror?

yup...  RAID1 mirror implemented in the intel raid bios...

---

### Post by jsylvia007 on 2014-02-08
> **jsylvia007 said:**
> yup...  RAID1 mirror implemented in the intel raid bios...

Any additional help here?

I'm thinking that maybe what I should do is remove the drive, put it in an external carrier, DD the whole drive with 0's.  Would that work?  Technically, wouldn't the RAID BIOS force a re-sync once it's added back in, or is it storing hard drive serial information which wouldn't kick off the rebuild process?

---

