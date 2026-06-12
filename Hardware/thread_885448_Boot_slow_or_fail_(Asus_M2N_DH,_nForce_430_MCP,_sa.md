---
title: "Boot slow or fail (Asus M2N DH, nForce 430 MCP, sata 2)"
date: 2008-08-10
forum: Hardware
---

### Post by Calimo on 2008-08-10
Boot slow or fail (Asus M2N DH, nForce 430 MCP, sata 2)

Hello,

I'm experiencing boot problems. Either it is slow (just now it took 4 minutes to show gdm login screen) or it fails. No problem when restarting.
I'm using 
- Ubuntu Hardy (8.04) (I already had some problems with Hardy, not with Gusty)
- Motherboard: Asus M2N DH (chipset nForce 430 MCP)
- 2 HD Sata2 Western Digital 7200 Caviar SE (16MB) of 160 & 250 Go.
/ is /dev/sdb1
/home is on /dev/sdb6


When it is slow, it hangs either when the start screen says "init-bottom" or "Reading files needed to boot".
Here is an interresting part of my dmesg : ```
[   19.013028] sata_nv 0000:00:08.0: version 3.5
[   19.013042] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [LSA0] -> GSI 20 (level, low) -> IRQ 19
[   19.013082] PCI: Setting latency timer of device 0000:00:08.0 to 64
[   19.013138] scsi0 : sata_nv
[   19.013301] scsi1 : sata_nv
[   19.013437] ata1: SATA max UDMA/133 cmd 0xe400 ctl 0xe080 bmdma 0xd880 irq 19
[   19.013439] ata2: SATA max UDMA/133 cmd 0xe000 ctl 0xdc00 bmdma 0xd888 irq 19
[   19.414118] usb 1-9: new high speed USB device using ehci_hcd and address 5
[   19.478459] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   19.486206] ata1.00: ATA-7: WDC WD1600JS-55NCB1, 10.02E01, max UDMA/133
[   19.486210] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   19.495185] ata1.00: configured for UDMA/133
[   19.552442] usb 1-9: configuration #1 chosen from 1 choice
[   19.854485] usb 2-3: new low speed USB device using ohci_hcd and address 2
[   19.961770] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   19.969524] ata2.00: ATA-7: WDC WD2500KS-00MJB0, 02.01C03, max UDMA/133
[   19.969530] ata2.00: 488397168 sectors, multi 16: LBA48 
[   19.978508] ata2.00: configured for UDMA/133
[   19.979027] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1600JS-55N 10.0 PQ: 0 ANSI: 5
[   19.979127] scsi 1:0:0:0: Direct-Access     ATA      WDC WD2500KS-00M 02.0 PQ: 0 ANSI: 5
[   19.979184] ACPI: PCI Interrupt 0000:00:08.1[B] -> Link [LSA1] -> GSI 23 (level, low) -> IRQ 16
[   19.979224] PCI: Setting latency timer of device 0000:00:08.1 to 64
[   19.979512] scsi2 : sata_nv
[   19.979642] scsi3 : sata_nv
[   19.979776] ata3: SATA max UDMA/133 cmd 0xd800 ctl 0xd480 bmdma 0xd000 irq 16
[   19.979778] ata4: SATA max UDMA/133 cmd 0xd400 ctl 0xd080 bmdma 0xd008 irq 16
[   20.067417] usb 2-3: configuration #1 chosen from 1 choice
[   20.289879] ata3: SATA link down (SStatus 0 SControl 300)
[   20.372769] usb 2-4: new low speed USB device using ohci_hcd and address 3
[   20.586727] usb 2-4: configuration #1 chosen from 1 choice
[   20.590669] usbcore: registered new interface driver hiddev
[   20.594818] input: BTC USB Multimedia Keyboard as /devices/pci0000:00/0000:00:02.0/usb2/2-3/2-3:1.0/input/input1
[   20.609431] ata4: SATA link down (SStatus 0 SControl 300)
[   20.619697] input,hidraw0: USB HID v1.10 Keyboard [BTC USB Multimedia Keyboard] on usb-0000:00:02.0-3
[   20.621633] pata_amd 0000:00:06.0: version 0.3.10
[   20.621678] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   20.621943] scsi4 : pata_amd
[   20.621992] scsi5 : pata_amd
[   20.622538] ata5: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[   20.622541] ata6: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[   20.630447] Driver 'sd' needs updating - please use bus_type methods
[   20.630526] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   20.630537] sd 0:0:0:0: [sda] Write Protect is off
[   20.630539] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   20.630553] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   20.630593] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   20.630601] sd 0:0:0:0: [sda] Write Protect is off
[   20.630603] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   20.630615] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   20.630619]  sda:<6>input: BTC USB Multimedia Keyboard as /devices/pci0000:00/0000:00:02.0/usb2/2-3/2-3:1.1/input/input2
[   20.638021]  sda1 sda2
[   20.638084] sd 0:0:0:0: [sda] Attached SCSI disk
[   20.638139] sd 1:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[   20.638150] sd 1:0:0:0: [sdb] Write Protect is off
[   20.638152] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   20.638166] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   20.638203] sd 1:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[   20.638211] sd 1:0:0:0: [sdb] Write Protect is off
[   20.638213] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   20.638225] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   20.638229]  sdb: sdb1 sdb2 <<6>input,hiddev96,hidraw1: USB HID v1.10 Device [BTC USB Multimedia Keyboard] on usb-0000:00:02.0-3
[   20.662935]  sdb5<6>input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:02.0/usb2/2-4/2-4:1.0/input/input3
[   20.670730]  sdb6 >
[   20.670817] sd 1:0:0:0: [sdb] Attached SCSI disk
[   20.675656] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   20.675675] sd 1:0:0:0: Attached scsi generic sg1 type 0
[   20.689392] input,hidraw2: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:02.0-4
[   20.689410] usbcore: registered new interface driver usbhid
[   20.689413] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   20.940679] ata5.00: ATAPI: Optiarc DVD RW AD-5170A, 1.13, max UDMA/66
[   21.050510] Attempting manual resume
[   21.050514] swsusp: Resume From Partition 8:21
[   21.050515] PM: Checking swsusp image.
[   21.050666] PM: Resume from disk failed.
[   21.097997] kjournald starting.  Commit interval 5 seconds
[   21.097592] EXT3-fs: mounted filesystem with ordered data mode.
[   21.112726] ata5.00: configured for UDMA/66
[   21.112762] ata6: port disabled. ignoring.
[   21.113756] scsi 4:0:0:0: CD-ROM            Optiarc  DVD RW AD-5170A  1.13 PQ: 0 ANSI: 5
[   21.113824] scsi 4:0:0:0: Attached scsi generic sg2 type 5
[   21.152296] Driver 'sr' needs updating - please use bus_type methods
[   21.156256] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[   21.156260] Uniform CD-ROM driver Revision: 3.20
[   21.156297] sr 4:0:0:0: Attached scsi CD-ROM sr0
[  202.286418] parport_pc 00:06: reported by Plug and Play ACPI
[  202.286472] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[  202.329098] parport0: Printer, HEWLETT-PACKARD DESKJET 895C
[  202.329455] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[  202.356520] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[  202.374732] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x600
[  202.374751] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x700
[  202.476126] input: Power Button (FF) as /devices/virtual/input/input4
[  202.571808] ACPI: Power Button (FF) [PWRF]
[  202.571879] input: Power Button (CM) as /devices/virtual/input/input5
[  202.627763] ACPI: Power Button (CM) [PWRB]
[  203.174383] Linux agpgart interface v0.102
[  203.437250] nvidia: module license 'NVIDIA' taints kernel.
[  203.719879] ACPI: PCI Interrupt Link [LNED] enabled at IRQ 19
[  203.719891] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNED] -> GSI 19 (level, low) -> IRQ 20
[  203.719898] PCI: Setting latency timer of device 0000:02:00.0 to 64
[  203.720115] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008
[  203.843669] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 22
[  203.843675] ACPI: PCI Interrupt 0000:00:05.0[B] -> Link [LAZA] -> GSI 22 (level, low) -> IRQ 17
[  203.843694] PCI: Setting latency timer of device 0000:00:05.0 to 64
[  203.882236] hda_codec: Unknown model for AD1988, trying auto-probe from BIOS...
[  204.254815] phy0: Selected rate control algorithm 'simple'
[  204.357757] phy0: hwaddr 00:15:af:0b:24:9c, rtl8187 V1 + rtl8225z2
[  204.357776] usbcore: registered new interface driver rtl8187
[  204.975948] lp0: using parport0 (interrupt-driven).
[  204.999079] it87: Found IT8716F chip at 0x290, revision 1
[  204.999091] it87: in3 is VCC (+5V)
[  204.999093] it87: in7 is VCCH (+5V Stand-By)
[  205.226763] Adding 2184800k swap on /dev/sdb5.  Priority:-1 extents:1 across:2184800k
[  205.947932] EXT3 FS on sdb1, internal journal
[  209.097918] kjournald starting.  Commit interval 5 seconds
[  209.098151] EXT3 FS on sdb6, internal journal
[  209.098155] EXT3-fs: mounted filesystem with ordered data mode.
```As you can see, nothing happens between 21 and 202 secs.


When it fails, I can see first Emask errors
```
[   65.660000] ata2.00: (BMDMA stat 0x24)
[   65.660000] ata2.00: cmd 25/00:20:87:83:38/00:02:00:00:00/e0 tag 0 cdb 0x0 data 278528 in
[   65.660000]          res 51/40:00:94:85:38/40:00:00:00:00/e0 Emask 0x9 (media error)
[   65.676000] ata2.00: configured for UDMA/133
[   65.676000] ata2: EH complete
[   83.996000] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   83.996000] ata2.00: (BMDMA stat 0x24)
(... continue 3/4 times)
```then```
ata 2.00: status: {DRDY ERR}
ata 2.00: err: {UNC}
```and then```
ata2: port is slow [...] (status 0x80)
COMRESET failed (errno=-16)
```and finally```
end_request: I/O error, dev sdb, sector 41424983 driverbyte=DRIVER_OK, SUGGEST_OK
```lines scrolling very fast.
I tried waiting (up to 10 minutes) but it never stops scrolling. So I restart with Alt+SysRq+REISUB, and it can also start slow or fail again.


I tried to add kernel arguments irqpoll and noapic nolapic acpi=off but it didn't solve the problem.

I also ran smartctl --test=long
```
xavier@ubuntu:~$ sudo smartctl -a /dev/sdb
smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar SE16 family
Device Model:     WDC WD2500KS-00MJB0
Serial Number:    WD-WCANKF400907
Firmware Version: 02.01C03
User Capacity:    250'059'350'016 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Sun Jun 22 09:10:27 2008 CEST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x84)    Offline data collection activity
                    was suspended by an interrupting command from host.
                    Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:          (8280) seconds.
Offline data collection
capabilities:              (0x7b) SMART execute Offline immediate.
                    Auto Offline data collection on/off support.
                    Suspend Offline collection upon new
                    command.
                    Offline surface scan supported.
                    Self-test supported.
                    Conveyance Self-test supported.
                    Selective Self-test supported.
SMART capabilities:            (0x0003)    Saves SMART data before entering
                    power-saving mode.
                    Supports SMART auto save timer.
Error logging capability:        (0x01)    Error logging supported.
                    General Purpose Logging supported.
Short self-test routine 
recommended polling time:      (   2) minutes.
Extended self-test routine
recommended polling time:      (  96) minutes.
Conveyance self-test routine
recommended polling time:      (   6) minutes.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   188   188   051    Pre-fail  Always       -       20556
  3 Spin_Up_Time            0x0003   195   189   021    Pre-fail  Always       -       5241
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       358
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   200   200   051    Pre-fail  Always       -       0
  9 Power_On_Hours          0x0032   098   098   000    Old_age   Always       -       1595
 10 Spin_Retry_Count        0x0013   100   100   051    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x0012   100   100   051    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       299
190 Temperature_Celsius     0x0022   060   050   045    Old_age   Always       -       40
194 Temperature_Celsius     0x0022   110   100   000    Old_age   Always       -       40
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   199   199   000    Old_age   Always       -       48
198 Offline_Uncorrectable   0x0010   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0009   197   179   051    Pre-fail  Offline      -       129

SMART Error Log Version: 1
ATA Error Count: 42 (device log contains only the most recent five errors)
    CR = Command Register [HEX]
    FR = Features Register [HEX]
    SC = Sector Count Register [HEX]
    SN = Sector Number Register [HEX]
    CL = Cylinder Low Register [HEX]
    CH = Cylinder High Register [HEX]
    DH = Device/Head Register [HEX]
    DC = Device Command Register [HEX]
    ER = Error register [HEX]
    ST = Status register [HEX]
Powered_Up_Time is measured from power on, and printed as
DDd+hh:mm:SS.sss where DD=days, hh=hours, mm=minutes,
SS=sec, and sss=millisec. It "wraps" after 49.710 days.

Error 42 occurred at disk power-on lifetime: 1593 hours (66 days + 9 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 b7 19 4c e0  Error: UNC at LBA = 0x004c19b7 = 4987319

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 38 8f 19 4c 00 00      00:09:21.298  READ DMA
  c8 00 08 87 19 4c 00 00      00:09:16.462  READ DMA
  c8 00 20 7f 83 77 02 00      00:09:16.456  READ DMA
  c8 00 08 87 00 74 02 00      00:09:12.530  READ DMA
  c8 00 08 f7 00 74 02 00      00:09:11.331  READ DMA

Error 41 occurred at disk power-on lifetime: 1593 hours (66 days + 9 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 60 19 4c e0  Error: UNC at LBA = 0x004c1960 = 4987232

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 5f 19 4c 00 00      00:03:40.200  READ DMA
  27 00 00 00 00 00 00 00      00:03:40.200  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 00 00      00:03:40.193  IDENTIFY DEVICE
  ef 03 46 00 00 00 00 00      00:03:40.193  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 00 00      00:03:40.193  READ NATIVE MAX ADDRESS EXT

Error 40 occurred at disk power-on lifetime: 1593 hours (66 days + 9 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 5f 19 4c e0  Error: UNC at LBA = 0x004c195f = 4987231

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 5f 19 4c 00 00      00:03:38.326  READ DMA
  27 00 00 00 00 00 00 00      00:03:38.326  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 00 00      00:03:38.318  IDENTIFY DEVICE
  ef 03 46 00 00 00 00 00      00:03:38.318  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 00 00      00:03:38.318  READ NATIVE MAX ADDRESS EXT

Error 39 occurred at disk power-on lifetime: 1593 hours (66 days + 9 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 5f 19 4c e0  Error: UNC at LBA = 0x004c195f = 4987231

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 5f 19 4c 00 00      00:03:36.397  READ DMA
  27 00 00 00 00 00 00 00      00:03:36.397  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 00 00      00:03:36.388  IDENTIFY DEVICE
  ef 03 46 00 00 00 00 00      00:03:36.388  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 00 00      00:03:36.388  READ NATIVE MAX ADDRESS EXT

Error 38 occurred at disk power-on lifetime: 1593 hours (66 days + 9 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 5f 19 4c e0  Error: UNC at LBA = 0x004c195f = 4987231

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 5f 19 4c 00 00      00:03:34.482  READ DMA
  27 00 00 00 00 00 00 00      00:03:34.482  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 00 00      00:03:34.475  IDENTIFY DEVICE
  ef 03 46 00 00 00 00 00      00:03:34.475  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 00 00      00:03:34.475  READ NATIVE MAX ADDRESS EXT

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%      1298         -
# 2  Extended offline    Aborted by host               90%      1274         -

SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.
```It looks ok to me...

What should I do to get my Ubuntu starting normally again ?
Thanks for your help !

Xavier

---

### Post by unc0nn3ct3d on 2008-09-04
That sucks that no one replied to your question.  I am encountering a similar problem and am considering running out to buy a new mobo and cpu.  Did you end up solving it?

---

### Post by Calimo on 2008-09-05
I didn't write earlier because I'm not sure the problem is really solved.
But I resized my windows sda1, made a 20GiB sda2, and installed Hardy on it (/home still on sdb6 and swap on sdb5). I didn't have any problems at boot, it always boots pretty quickly (no hang on init-bottom or files needed to boot).

What is most strange is that even the Ubuntu that is still on sdb1 boots well ! I can't understand this (was this problem caused by the grub file that was on sdb1/boot? Doesn't make sense to me).

If I'm gutsy enough, I will eventually resize sdb2 to a few hundred of MiB, and reinstall Hardy on sdb1 with /boot on sda2 and /home on sdb6 to see if it works well.

---

