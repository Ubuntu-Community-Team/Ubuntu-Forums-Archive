---
title: "my home partition gets periodiccally remounted readonly (no apparent HDD failure)"
date: 2012-02-18
forum: Hardware
---

### Post by cideous on 2012-02-18
Hello,

always after runnung ubuntu for a few days, I get the problem that the kernel gets a problem with my home partition and remounts it readonly. I actually cannot remount it readwrite again, but have to reboot the system. This rebooting causes some orphaned inodes to be found on the reboot, but I cannot determin any errors on the harddisk. No errors in SMART, etc. The laptop is acutally very new, and the error reoccurs since I got the laptop.

I am really puzzled by the error message given by `dmesg` (see below). Can you tell me what this actually means? I found several bug reports with similar problems than produced by my dmesg, they mostly seemed hardware specific and none that I found matched my hardware.

Output of lspci
```

# lspci -v
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
        Subsystem: Micro-Star International Co., Ltd. Device 10a0
        Flags: bus master, fast devsel, latency 0
        Capabilities: [e0] Vendor Specific Information: Len=0c <?>

00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 0000e000-0000efff
        Memory behind bridge: f4000000-f60fffff
        Prefetchable memory behind bridge: 00000000e0000000-00000000ebffffff
        Capabilities: [88] Subsystem: Micro-Star International Co., Ltd. Device 10a0
        Capabilities: [80] Power Management version 3
        Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
        Capabilities: [a0] Express Root Port (Slot+), MSI 00
        Capabilities: [100] Virtual Channel
        Capabilities: [140] Root Complex Link
        Kernel driver in use: pcieport
        Kernel modules: shpchp

00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
        Subsystem: Micro-Star International Co., Ltd. Device 10a0
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at f630a000 (64-bit, non-prefetchable) [size=16]
        Capabilities: [50] Power Management version 3
        Capabilities: [8c] MSI: Enable- Count=1/1 Maskable- 64bit+
        Kernel driver in use: mei
        Kernel modules: mei

00:1a.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05) (prog-if 20 [EHCI])
        Subsystem: Micro-Star International Co., Ltd. Device 10a0
        Flags: bus master, medium devsel, latency 0, IRQ 16
        Memory at f6308000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [50] Power Management version 2
        Capabilities: [58] Debug port: BAR=1 offset=00a0
        Capabilities: [98] PCI Advanced Features
        Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
        Subsystem: Micro-Star International Co., Ltd. Device 10ab
        Flags: bus master, fast devsel, latency 0, IRQ 55
        Memory at f6300000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
        Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
        Capabilities: [100] Virtual Channel
        Capabilities: [130] Root Complex Link
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 0000d000-0000dfff
        Prefetchable memory behind bridge: 00000000ec100000-00000000ec1fffff
        Capabilities: [40] Express Root Port (Slot+), MSI 00
        Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
        Capabilities: [90] Subsystem: Micro-Star International Co., Ltd. Device 10a0
        Capabilities: [a0] Power Management version 2
        Kernel driver in use: pcieport
        Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b5) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        Memory behind bridge: f6200000-f62fffff
        Capabilities: [40] Express Root Port (Slot+), MSI 00
        Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
        Capabilities: [90] Subsystem: Micro-Star International Co., Ltd. Device 10a0
        Capabilities: [a0] Power Management version 2
        Kernel driver in use: pcieport
        Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        Memory behind bridge: f6100000-f61fffff
        Capabilities: [40] Express Root Port (Slot+), MSI 00
        Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
        Capabilities: [90] Subsystem: Micro-Star International Co., Ltd. Device 10a0
        Capabilities: [a0] Power Management version 2
        Kernel driver in use: pcieport
        Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05) (prog-if 20 [EHCI])
        Subsystem: Micro-Star International Co., Ltd. Device 10a0
        Flags: bus master, medium devsel, latency 0, IRQ 23
        Memory at f6307000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [50] Power Management version 2
        Capabilities: [58] Debug port: BAR=1 offset=00a0
        Capabilities: [98] PCI Advanced Features
        Kernel driver in use: ehci_hcd

00:1f.0 ISA bridge: Intel Corporation HM67 Express Chipset Family LPC Controller (rev 05)
        Subsystem: Micro-Star International Co., Ltd. Device 10a0
        Flags: bus master, medium devsel, latency 0
        Capabilities: [e0] Vendor Specific Information: Len=0c <?>
        Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05) (prog-if 01 [AHCI 1.0])
        Subsystem: Micro-Star International Co., Ltd. Device 10a0
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 53
        I/O ports at f070 [size=8]
        I/O ports at f060 [size=4]
        I/O ports at f050 [size=8]
        I/O ports at f040 [size=4]
        I/O ports at f020 [size=32]
        Memory at f6306000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
        Capabilities: [70] Power Management version 3
        Capabilities: [a8] SATA HBA v1.0
        Capabilities: [b0] PCI Advanced Features
        Kernel driver in use: ahci
        Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
        Subsystem: Micro-Star International Co., Ltd. Device 10a0
        Flags: medium devsel, IRQ 4
        Memory at f6305000 (64-bit, non-prefetchable) [size=256]
        I/O ports at f000 [size=32]
        Kernel modules: i2c-i801

01:00.0 VGA compatible controller: nVidia Corporation Device 1210 (rev a1) (prog-if 00 [VGA controller])
        Subsystem: Micro-Star International Co., Ltd. Device 10bd
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at f4000000 (32-bit, non-prefetchable) [size=32M]
        Memory at e0000000 (64-bit, prefetchable) [size=128M]
        Memory at e8000000 (64-bit, prefetchable) [size=64M]
        I/O ports at e000 [size=128]
        [virtual] Expansion ROM at f6000000 [disabled] [size=512K]
        Capabilities: [60] Power Management version 3
        Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
        Capabilities: [78] Express Endpoint, MSI 00
        Capabilities: [b4] Vendor Specific Information: Len=14 <?>
        Capabilities: [100] Virtual Channel
        Capabilities: [128] Power Budgeting <?>
        Capabilities: [600] Vendor Specific Information: ID=0001 Rev=1 Len=024 <?>
        Kernel driver in use: nvidia
        Kernel modules: nvidia_current, nouveau, nvidiafb

01:00.1 Audio device: nVidia Corporation Device 0e0c (rev a1)
        Subsystem: Micro-Star International Co., Ltd. Device 10bd
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at f6080000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: [60] Power Management version 3
        Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
        Capabilities: [78] Express Endpoint, MSI 00
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
        Subsystem: Micro-Star International Co., Ltd. Device 10a0
        Flags: bus master, fast devsel, latency 0, IRQ 54
        I/O ports at d000 [size=256]
        Memory at ec104000 (64-bit, prefetchable) [size=4K]
        Memory at ec100000 (64-bit, prefetchable) [size=16K]
        Capabilities: [40] Power Management version 3
        Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
        Capabilities: [70] Express Endpoint, MSI 01
        Capabilities: [b0] MSI-X: Enable- Count=4 Masked-
        Capabilities: [d0] Vital Product Data
        Capabilities: [100] Advanced Error Reporting
        Capabilities: [140] Virtual Channel
        Capabilities: [160] Device Serial Number 01-00-00-00-68-4c-e0-00
        Kernel driver in use: r8169
        Kernel modules: r8169

03:00.0 Network controller: Intel Corporation Centrino Wireless-N 130 (rev 34)
        Subsystem: Intel Corporation Centrino Wireless-N 130 BGN
        Flags: bus master, fast devsel, latency 0, IRQ 56
        Memory at f6200000 (64-bit, non-prefetchable) [size=8K]
        Capabilities: [c8] Power Management version 3
        Capabilities: [d0] MSI: Enable+ Count=1/1 Maskable- 64bit+
        Capabilities: [e0] Express Endpoint, MSI 00
        Capabilities: [100] Advanced Error Reporting
        Capabilities: [140] Device Serial Number dc-a9-71-ff-ff-a1-f9-b4
        Kernel driver in use: iwlagn
        Kernel modules: iwlagn

04:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04) (prog-if 30 [XHCI])
        Subsystem: Micro-Star International Co., Ltd. Device 10a0
        Flags: bus master, fast devsel, latency 0, IRQ 19
        Memory at f6100000 (64-bit, non-prefetchable) [size=8K]
        Capabilities: [50] Power Management version 3
        Capabilities: [70] MSI: Enable- Count=1/8 Maskable- 64bit+
        Capabilities: [90] MSI-X: Enable+ Count=8 Masked-
        Capabilities: [a0] Express Endpoint, MSI 00
        Capabilities: [100] Advanced Error Reporting
        Capabilities: [140] Device Serial Number ff-ff-ff-ff-ff-ff-ff-ff
        Capabilities: [150] #18
        Kernel driver in use: xhci_hcd
        Kernel modules: xhci-hcd

```dmesg output: 
```

[46459.069586] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[46459.069597] ata2.00: failed command: FLUSH CACHE EXT
[46459.069610] ata2.00: cmd ea/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[46459.069613]          res 40/00:00:00:4f:c2/00:00:00:00:00/00 Emask 0x4 (timeout)
[46459.069619] ata2.00: status: { DRDY }
[46459.069630] ata2: hard resetting link
[46464.421564] ata2: link is slow to respond, please be patient (ready=0)
[46469.062649] ata2: COMRESET failed (errno=-16)
[46469.062660] ata2: hard resetting link
[46474.414664] ata2: link is slow to respond, please be patient (ready=0)
[46479.055752] ata2: COMRESET failed (errno=-16)
[46479.055764] ata2: hard resetting link
[46484.407796] ata2: link is slow to respond, please be patient (ready=0)
[46499.526668] type=1400 audit(1329582010.020:992): apparmor="DENIED" operation="mknod" parent=1039 profile="/sbin/dhclient" name="/home/var/lib/dhcp/dhclient-d9e6b358-e34f-470c-b745-8a2df9759bd1-eth0.lease" pid=1568 comm="dhclient" requested_mask="c" denied_mask="c" fsuid=0 ouid=0
[46511.449001] type=1400 audit(1329582021.960:993): apparmor="DENIED" operation="mknod" parent=2366 profile="/sbin/dhclient" name="/home/var/lib/dhcp/dhclient.leases" pid=11675 comm="dhclient" requested_mask="c" denied_mask="c" fsuid=0 ouid=0
[46514.043679] ata2: COMRESET failed (errno=-16)
[46514.043692] ata2: limiting SATA link speed to 1.5 Gbps
[46514.043697] ata2: hard resetting link
[46519.060228] ata2: COMRESET failed (errno=-16)
[46519.060239] ata2: reset failed, giving up
[46519.060245] ata2.00: disabled
[46519.060254] ata2.00: device reported invalid CHS sector 0
[46519.060271] ata2: EH complete
[46519.060359] sd 1:0:0:0: [sdb] Unhandled error code
[46519.060365] sd 1:0:0:0: [sdb]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[46519.060373] sd 1:0:0:0: [sdb] CDB: Write(10): 2a 00 57 42 99 c0 00 00 08 00
[46519.060393] end_request: I/O error, dev sdb, sector 1463982528
[46519.060400] end_request: I/O error, dev sdb, sector 1463982528
[46519.060427] sd 1:0:0:0: [sdb] Unhandled error code
[46519.060432] Aborting journal on device sdb8-8.
[46519.060440] sd 1:0:0:0: [sdb]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[46519.060449] sd 1:0:0:0: [sdb] CDB: Read(10): 28 00 4b 39 9d e0 00 02 00 00
[46519.060472] end_request: I/O error, dev sdb, sector 1262067168
[46519.060502] sd 1:0:0:0: [sdb] Unhandled error code
[46519.060509] sd 1:0:0:0: [sdb]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[46519.060519] sd 1:0:0:0: [sdb] CDB: 
[46519.060525] sd 1:0:0:0: [sdb] Unhandled error code
[46519.060530] sd 1:0:0:0: [sdb]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[46519.060538] sd 1:0:0:0: [sdb] CDB: Write(10): 2a 00 49 91 64 10 00 00 10 00
[46519.060555] end_request: I/O error, dev sdb, sector 1234265104
[46519.060561] Write(10)
[46519.060566] Buffer I/O error on device sdb8, logical block 32162690
[46519.060571] : 2a 00
[46519.060581] Buffer I/O error on device sdb8, logical block 32162691
[46519.060585]  57 3f 48 00 00 00 08 00
[46519.060599] end_request: I/O error, dev sdb, sector 1463764992
[46519.060602] EXT4-fs warning (device sdb8): ext4_end_bio:258: I/O error writing to inode 7997615 (offset 0 size 8192 starting block 154283140)
[46519.060605] Buffer I/O error on device sdb8, logical block 60850176
[46519.060606] sd 1:0:0:0: [sdb] Unhandled error code
[46519.060607] sd 1:0:0:0: [sdb]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[46519.060609] sd 1:0:0:0: [sdb] CDB: Write(10): 2a 00 4a 40 6a e8 00 00 08 00
[46519.060613] end_request: I/O error, dev sdb, sector 1245735656
[46519.060615] lost page write due to I/O error on sdb8
[46519.060616] Buffer I/O error on device sdb8, logical block 33596509
[46519.060620] EXT4-fs warning (device sdb8): ext4_end_bio:258: I/O error writing to inode 8520021 (offset 0 size 4096 starting block 155716958)
[46519.060638] JBD2: I/O error detected when updating journal superblock for sdb8-8.
[46519.060649] sd 1:0:0:0: [sdb] Unhandled error code
[46519.060650] journal commit I/O error
[46519.060652] sd 1:0:0:0: [sdb]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[46519.060654] sd 1:0:0:0: [sdb] CDB: Read(10): 28 00 4b 39 9d e0 00 00 08 00
[46519.060658] end_request: I/O error, dev sdb, sector 1262067168
[46519.060682] sd 1:0:0:0: [sdb] Unhandled error code
[46519.060683] sd 1:0:0:0: [sdb] Unhandled error code
[46519.060685] sd 1:0:0:0: [sdb]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[46519.060686] sd 1:0:0:0: [sdb] CDB: Write(10): 2a 00 3a 3b 48 00 00 00 08 00
[46519.060690] end_request: I/O error, dev sdb, sector 976963584
[46519.060692] sd 1:0:0:0: [sdb]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[46519.060693] sd 1:0:0:0: [sdb] CDB: Read(10): 28 00 4b 39 9d e0 00 00 08 00
[46519.060697] end_request: I/O error, dev sdb, sector 1262067168
[46519.060698] Buffer I/O error on device sdb8, logical block 0
[46519.060700] lost page write due to I/O error on sdb8
[46519.060707] EXT4-fs error (device sdb8): ext4_journal_start_sb:296: Detected aborted journal
[46519.060710] EXT4-fs (sdb8): Remounting filesystem read-only
[46519.060712] EXT4-fs (sdb8): previous I/O error to superblock detected

```before that smipped from dmesg I get repeatly thousands outputs of the for:
```

[46449.608032] type=1400 audit(1329581960.028:991): apparmor="DENIED" operation="mknod" parent=1039 profile="/sbin/dhclient" name="/home/var/lib/dhcp/dhclient-d9e6b358-e34f-470c-b745-8a2df9759bd1-eth0.lease" pid=1568 comm="dhclient" requested_mask="c" denied_mask="c" fsuid=0 ouid=

```I don't see how that could be causing my problem, I believe it is unrelated, it refers to the bug
[https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/810270](https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/810270)
and as I read it, is still an open bug for dhclient.

After the above snipped my logfile is spammed with repetitions of this error
```

[46519.067875] sd 1:0:0:0: [sdb] Unhandled error code
[46519.067877] sd 1:0:0:0: [sdb]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[46519.067879] sd 1:0:0:0: [sdb] CDB: Read(10): 28 00 4b 61 48 00 00 00 08 00

```which I believe is just a consequence of the above.

Now what should be relavant to this issue is my hardware configuration. My laptop is a **`XMG P711**`, which si probably not very famous. Its essentially a barebone with very cutting edge hardware. I hope you don;t decline my problem just because of this.



Output from SMART, which I believe shows no issues, also the extended test didn't produce any errors:
```

smartctl --all /dev/sdb
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.0.0-15-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Device Model:     SAMSUNG HN-M101MBB
Serial Number:    S2R8J9BB910736
LU WWN Device Id: 5 0024e9 206233df5
Firmware Version: 2AR10001
User Capacity:    1,000,204,886,016 bytes [1.00 TB]
Sector Size:      512 bytes logical/physical
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 6
Local Time is:    Sat Feb 18 18:11:08 2012 CET
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00) Offline data collection activity
                                        was never started.
                                        Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever 
                                        been run.
Total time to complete Offline 
data collection:                (13440) seconds.
Offline data collection
capabilities:                    (0x5b) SMART execute Offline immediate.
                                        Auto Offline data collection on/off support.
                                        Suspend Offline collection upon new
                                        command.
                                        Offline surface scan supported.
                                        Self-test supported.
                                        No Conveyance Self-test supported.
                                        Selective Self-test supported.
SMART capabilities:            (0x0003) Saves SMART data before entering
                                        power-saving mode.
                                        Supports SMART auto save timer.
Error logging capability:        (0x01) Error logging supported.
                                        General Purpose Logging supported.
Short self-test routine 
recommended polling time:        (   2) minutes.
Extended self-test routine
recommended polling time:        ( 224) minutes.
SCT capabilities:              (0x003f) SCT Status supported.
                                        SCT Error Recovery Control supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   100   100   051    Pre-fail  Always       -       1
  2 Throughput_Performance  0x0026   055   055   000    Old_age   Always       -       12231
  3 Spin_Up_Time            0x0023   089   089   025    Pre-fail  Always       -       3465
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       128
  5 Reallocated_Sector_Ct   0x0033   252   252   010    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   252   252   051    Old_age   Always       -       0
  8 Seek_Time_Performance   0x0024   252   252   015    Old_age   Offline      -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       162
 10 Spin_Retry_Count        0x0032   252   252   051    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       40
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       127
181 Program_Fail_Cnt_Total  0x0022   100   100   000    Old_age   Always       -       18926624
191 G-Sense_Error_Rate      0x0022   100   100   000    Old_age   Always       -       3
192 Power-Off_Retract_Count 0x0022   252   252   000    Old_age   Always       -       0
194 Temperature_Celsius     0x0002   064   057   000    Old_age   Always       -       33 (Min/Max 19/43)
195 Hardware_ECC_Recovered  0x003a   100   100   000    Old_age   Always       -       0
196 Reallocated_Event_Count 0x0032   252   252   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   252   252   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   252   252   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0036   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x002a   100   100   000    Old_age   Always       -       404
223 Load_Retry_Count        0x0032   100   100   000    Old_age   Always       -       40
225 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       5127

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%       158         -
# 2  Short offline       Completed without error       00%       149         -
# 3  Extended offline    Aborted by host               90%       148         -

Note: selective self-test log revision number (0) not 1 implies that no selective self-test has ever been run
SMART Selective self-test log data structure revision number 0
Note: revision number not 1 implies that no selective self-test has ever been run
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Completed [00% left] (0-65535)
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.

```

Thank you for any ideas. And I can produce any other output that might help to analyse this issue?

---

### Post by gordintoronto on 2012-02-18
Why is your hard drive SDB? What version of Ubuntu?

If you're not using the latest version of Ubuntu, you should try it. Running the latest hardware on an old OS often causes grief.

---

### Post by cideous on 2012-02-19
My harddisk is sdb because sda is an SSD hard disk. I store many things on sdb because it has much more storage and with SSDs you should be careful about the rewrites. My root partition is on sda though.

I am runnung the latest version of (k)ubuntu (11.10).

---

### Post by gordintoronto on 2012-02-19
How big is the hard drive? Is it using GPT?

Could you open a terminal window and enter the command:
df -h
(this should show the partition sizes and usage)
It appears that sdb8 is /home?

---

### Post by cideous on 2012-02-20
Output of `df -h`
```

/dev/sda2              37G  7.8G   29G  22% /
udev                  7.9G   12K  7.9G   1% /dev
tmpfs                 3.2G  936K  3.2G   1% /run
none                  5.0M     0  5.0M   0% /run/lock
none                  7.9G  3.4M  7.9G   1% /run/shm
/dev/sdb8             459G   69G  391G  15% /home

```

The /home is on an extended partition on sdb. Its not a GPT partition, I created all partions myself with fdisk and at least as I understand it, its not GPT as long as I don't use some special tools.

---

