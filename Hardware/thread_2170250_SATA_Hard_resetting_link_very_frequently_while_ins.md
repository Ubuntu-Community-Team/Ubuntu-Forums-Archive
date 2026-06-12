---
title: "SATA Hard resetting link very frequently while installing"
date: 2013-08-25
forum: Hardware
---

### Post by daniel54 on 2013-08-25
Hello,

I've installed 13.04 on my Toshiba Qosmio x505. I have two sata drives inside (it's big laptop) 
1. Samsung SSD 830 128GB
2. WD 7500BPKT 750GB

While installing ubuntu i saw this output very frequently:

```
Aug 25 16:57:43 ubuntu kernel: [  903.883388] ata5: hard resetting link
Aug 25 16:57:44 ubuntu /plugininstall.py: log-output -t ubiquity chroot /target mount -t proc proc /proc
Aug 25 16:57:44 ubuntu /plugininstall.py: log-output -t ubiquity chroot /target mount -t sysfs sysfs /sys
Aug 25 16:57:44 ubuntu /plugininstall.py: log-output -t ubiquity chroot /target mount -t securityfs securityfs /sys/kernel/security
Aug 25 16:57:44 ubuntu ubiquity:  * Recaching AppArmor profiles
Aug 25 16:57:44 ubuntu ubiquity: Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
Aug 25 16:57:44 ubuntu ubiquity: Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
Aug 25 16:57:44 ubuntu kernel: [  904.606319] ata5: SATA link down (SStatus 0 SControl 310)
Aug 25 16:57:44 ubuntu kernel: [  904.622311] ata5: EH complete
Aug 25 16:57:44 ubuntu kernel: [  904.681470] ata5: exception Emask 0x10 SAct 0x0 SErr 0x4000000 action 0xe frozen
Aug 25 16:57:44 ubuntu kernel: [  904.681474] ata5: irq_stat 0x00000040, connection status changed
Aug 25 16:57:44 ubuntu kernel: [  904.681476] ata5: SError: { DevExch }
Aug 25 16:57:44 ubuntu kernel: [  904.681481] ata5: limiting SATA link speed to 1.5 Gbps
Aug 25 16:57:44 ubuntu kernel: [  904.681484] ata5: hard resetting link
Aug 25 16:57:45 ubuntu kernel: [  905.402069] ata5: SATA link down (SStatus 0 SControl 310)
Aug 25 16:57:45 ubuntu kernel: [  905.418041] ata5: EH complete
Aug 25 16:57:45 ubuntu kernel: [  905.479563] ata5: exception Emask 0x10 SAct 0x0 SErr 0x4000000 action 0xe frozen
Aug 25 16:57:45 ubuntu kernel: [  905.479566] ata5: irq_stat 0x00000040, connection status changed
Aug 25 16:57:45 ubuntu kernel: [  905.479568] ata5: SError: { DevExch }
Aug 25 16:57:45 ubuntu kernel: [  905.479574] ata5: limiting SATA link speed to 1.5 Gbps
Aug 25 16:57:45 ubuntu kernel: [  905.479576] ata5: hard resetting link
Aug 25 16:57:46 ubuntu kernel: [  906.201810] ata5: SATA link down (SStatus 0 SControl 310)
Aug 25 16:57:46 ubuntu kernel: [  906.217798] ata5: EH complete
Aug 25 16:57:46 ubuntu kernel: [  906.277655] ata5: exception Emask 0x10 SAct 0x0 SErr 0x4000000 action 0xe frozen
Aug 25 16:57:46 ubuntu kernel: [  906.277658] ata5: irq_stat 0x00000040, connection status changed
Aug 25 16:57:46 ubuntu kernel: [  906.277660] ata5: SError: { DevExch }
Aug 25 16:57:46 ubuntu kernel: [  906.277666] ata5: limiting SATA link speed to 1.5 Gbps
Aug 25 16:57:46 ubuntu kernel: [  906.277668] ata5: hard resetting link
Aug 25 16:57:46 ubuntu kernel: [  906.997556] ata5: SATA link down (SStatus 0 SControl 310)
Aug 25 16:57:46 ubuntu kernel: [  907.013526] ata5: EH complete
Aug 25 16:57:47 ubuntu kernel: [  907.075756] ata5: exception Emask 0x10 SAct 0x0 SErr 0x4000000 action 0xe frozen
Aug 25 16:57:47 ubuntu kernel: [  907.075759] ata5: irq_stat 0x00000040, connection status changed
Aug 25 16:57:47 ubuntu kernel: [  907.075761] ata5: SError: { DevExch }
Aug 25 16:57:47 ubuntu kernel: [  907.075767] ata5: limiting SATA link speed to 1.5 Gbps
Aug 25 16:57:47 ubuntu kernel: [  907.075769] ata5: hard resetting link
Aug 25 16:57:47 ubuntu kernel: [  907.797294] ata5: SATA link down (SStatus 0 SControl 310)
Aug 25 16:57:47 ubuntu kernel: [  907.813282] ata5: EH complete
Aug 25 16:57:47 ubuntu kernel: [  907.873853] ata5: exception Emask 0x10 SAct 0x0 SErr 0x4000000 action 0xe frozen
Aug 25 16:57:47 ubuntu kernel: [  907.873857] ata5: irq_stat 0x00000040, connection status changed
Aug 25 16:57:47 ubuntu kernel: [  907.873859] ata5: SError: { DevExch }
Aug 25 16:57:47 ubuntu kernel: [  907.873865] ata5: limiting SATA link speed to 1.5 Gbps
Aug 25 16:57:47 ubuntu kernel: [  907.873867] ata5: hard resetting link
Aug 25 16:57:48 ubuntu kernel: [  908.597044] ata5: SATA link down (SStatus 0 SControl 310)
Aug 25 16:57:48 ubuntu kernel: [  908.613024] ata5: EH complete
Aug 25 16:57:48 ubuntu kernel: [  908.671946] ata5: exception Emask 0x10 SAct 0x0 SErr 0x4000000 action 0xe frozen
Aug 25 16:57:48 ubuntu kernel: [  908.671950] ata5: irq_stat 0x00000040, connection status changed
Aug 25 16:57:48 ubuntu kernel: [  908.671952] ata5: SError: { DevExch }
Aug 25 16:57:48 ubuntu kernel: [  908.671958] ata5: limiting SATA link speed to 1.5 Gbps
Aug 25 16:57:48 ubuntu kernel: [  908.671960] ata5: hard resetting link
```

Is something very bad with my SSD/Motherboard or it's normal?

Regards

---

### Post by daniel54 on 2013-08-26
Thread went down with 110 views. Don't make me think that ubuntu specialists on this forum don't know what's wrong.

Bump

---

### Post by Yellow Pasque on 2013-08-26
1. Check for BIOS update
2. Look at the rest of dmesg to figure out which drive is ata5 and is giving the errors
3. Don't bump more than once per 24 hours

---

### Post by daniel54 on 2013-08-26
Hello,

1.Bios is already in newest version
2. It seems that ATA9 is SSD and ATA9 is WD 7500. I don't know how to find ATA5 in this file so im attaching it [http://speedy.sh/39aQu/syslog.zip](http://speedy.sh/39aQu/syslog.zip)
3.OK

Fdisk -l ```
root@kamaz-Qosmio-X505:/usr# fdisk -l

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x5faa27f3


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048  1465145343   732571648    7  HPFS/NTFS/exFAT


Disk /dev/sdb: 128.0 GB, 128035676160 bytes
255 heads, 63 sectors/track, 15566 cylinders, total 250069680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9060192a


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   184540023    92268988    7  HPFS/NTFS/exFAT
/dev/sdb2       184541182   250068991    32763905    5  Extended
/dev/sdb5       184541184   241719295    28589056   83  Linux
/dev/sdb6       241721344   250068991     4173824   82  Linux swap / Solaris


Disk /dev/mapper/cryptswap1: 4273 MB, 4273995776 bytes
255 heads, 63 sectors/track, 519 cylinders, total 8347648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2ab99232


Disk /dev/mapper/cryptswap1 doesn't contain a valid partition table

```

Windows chkdsk reports no problems with filesystem on its partitions

Regards

---

### Post by Yellow Pasque on 2013-08-26
What I meant was this:
```
ata1.00: ATA-8: WDC WD7500BPKT-00PK4T0, 01.01A01, max UDMA/133
ata2.00: ATA-9: SAMSUNG SSD 830 Series, CXM03B1Q, max UDMA/133
```

So ata5.00 port is hooked to... nothing? eSATA? An optical drive?

---

### Post by daniel54 on 2013-08-26
I don't know. I thought that you will tell me :)

---

### Post by Yellow Pasque on 2013-08-26
Unless I'm missing it, the log doesn't indicate that anything is hooked to that port. Let me put it another way...
Do you have an optical drive or some other storage device you use other than the Samsung and the WD7500?

---

### Post by daniel54 on 2013-08-26
Yes i have optical drive connected inside the laptop.

---

### Post by Yellow Pasque on 2013-08-26
Have you tried using the optical drive? Is it giving you any issues?

---

### Post by daniel54 on 2013-08-26
Sorry that i didn't told you earlier but i thought that's not important. My optical drive is damaged from the beginning but as far as i know optical drives are still connected by old ATA, not SATA. Maybe im wrong.

Regards

---

### Post by Yellow Pasque on 2013-08-26
See if your BIOS allows you to disable individual SATA ports (and yes, your optical drive is probably connected via SATA).

---

### Post by daniel54 on 2013-08-26
It doesn't, i have to remove optical drive physically.

When i did it where can i test has that error dissapeared?

Regards

---

### Post by Yellow Pasque on 2013-08-26
Check:
```
dmesg
```

I'm not sure if removing the drive is worthwhile. You may want to google for ways to suppress the error message if it's not causing any harm other than spamming the log.

---

### Post by daniel54 on 2013-09-07
Hello,

I've still didnt removed the drive because i had no time but i found more info in today log:

```

[    1.127102] [Firmware Bug]: ACPI(VGA) defines _DOD but not _DOS
[    1.127892] acpi device:2e: registered as cooling_device8
[    1.127918] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[    1.127965] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:2c/LNXVIDEO:00/input/input4
[    1.129039] ahci 0000:00:1f.2: version 3.0
[    1.129104] ahci 0000:00:1f.2: irq 49 for MSI/MSI-X
[    1.129138] ahci: SSS flag set, parallel bus scan disabled
[    1.144078] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x3b impl SATA mode
[    1.144090] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pio slum part ems sxs apst 
[    1.144096] ahci 0000:00:1f.2: setting latency timer to 64
[    1.152085] mmc0: SDHCI controller on PCI [0000:08:00.1] using ADMA
[    1.161873] atl1c 0000:10:00.0: version 1.0.1.1-NAPI
[    1.176369] scsi0 : ahci
[    1.176450] scsi1 : ahci
[    1.176511] scsi2 : ahci
[    1.176590] scsi3 : ahci
[    1.176672] scsi4 : ahci
[    1.176749] scsi5 : ahci
[    1.176785] ata1: SATA max UDMA/133 abar m2048@0xc8408000 port 0xc8408100 irq 49
[    1.176788] ata2: SATA max UDMA/133 abar m2048@0xc8408000 port 0xc8408180 irq 49
[    1.176790] ata3: DUMMY
[    1.176793] ata4: SATA max UDMA/133 abar m2048@0xc8408000 port 0xc8408280 irq 49
[    1.176796] ata5: SATA max UDMA/133 abar m2048@0xc8408000 port 0xc8408300 irq 49
[    1.176798] ata6: SATA max UDMA/133 abar m2048@0xc8408000 port 0xc8408380 irq 49
[    1.208093] firewire_ohci 0000:08:00.0: added OHCI v1.10 device as card 0, 8 IR + 8 IT contexts, quirks 0x10
[    1.284039] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    1.416533] usb 1-1: New USB device found, idVendor=8087, idProduct=0024
[    1.416536] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.416989] hub 1-1:1.0: USB hub found
[    1.417173] hub 1-1:1.0: 6 ports detected
[    1.495980] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.527968] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    1.553375] ata1.00: ATA-8: WDC WD7500BPKT-00PK4T0, 01.01A01, max UDMA/133
[    1.553386] ata1.00: 1465149168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    1.556028] ata1.00: configured for UDMA/133
[    1.556179] scsi 0:0:0:0: Direct-Access     ATA      WDC WD7500BPKT-0 01.0 PQ: 0 ANSI: 5
[    1.556322] sd 0:0:0:0: [sda] 1465149168 512-byte logical blocks: (750 GB/698 GiB)
[    1.556325] sd 0:0:0:0: [sda] 4096-byte physical blocks
[    1.556362] sd 0:0:0:0: [sda] Write Protect is off
[    1.556364] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.556366] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.556379] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.575157]  sda: sda1
[    1.575414] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.660489] usb 2-1: New USB device found, idVendor=8087, idProduct=0024
[    1.660493] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.660881] hub 2-1:1.0: USB hub found
[    1.660958] hub 2-1:1.0: 6 ports detected
[    1.708082] firewire_core 0000:08:00.0: created device fw0: GUID 001b240001d3ad9c, S400
[    1.732133] usb 1-1.4: new high-speed USB device number 3 using ehci-pci
[    1.830466] usb 1-1.4: New USB device found, idVendor=04f2, idProduct=b130
[    1.830477] usb 1-1.4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.830483] usb 1-1.4: Product: USB2.0 UVC WebCam
[    1.830488] usb 1-1.4: Manufacturer: Chicony
[    1.830493] usb 1-1.4: SerialNumber: CNA8155-000001
[    1.875860] ata2: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    1.876525] ata2.00: ATA-9: SAMSUNG SSD 830 Series, CXM03B1Q, max UDMA/133
[    1.876534] ata2.00: 250069680 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.877025] ata2.00: configured for UDMA/133
[    1.877281] scsi 1:0:0:0: Direct-Access     ATA      SAMSUNG SSD 830  CXM0 PQ: 0 ANSI: 5
[    1.877438] sd 1:0:0:0: [sdb] 250069680 512-byte logical blocks: (128 GB/119 GiB)
[    1.877493] sd 1:0:0:0: [sdb] Write Protect is off
[    1.877496] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.877508] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.877522] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    1.878852]  sdb: sdb1 sdb2 < sdb5 sdb6 sdb7 >
[    1.879201] sd 1:0:0:0: [sdb] Attached SCSI disk
[    1.904084] usb 1-1.6: new full-speed USB device number 4 using ehci-pci
[    1.911827] tsc: Refined TSC clocksource calibration: 1995.466 MHz
[    1.911847] Switching to clocksource tsc
[    1.996945] usb 1-1.6: New USB device found, idVendor=0930, idProduct=0215
[    1.996956] usb 1-1.6: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.067812] usb 2-1.2: new full-speed USB device number 3 using ehci-pci
[    2.162005] usb 2-1.2: New USB device found, idVendor=e0ff, idProduct=0002
[    2.162016] usb 2-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.162022] usb 2-1.2: Product: G3
[    2.162027] usb 2-1.2: Manufacturer: A.....
[    2.170114] usbcore: registered new interface driver usbhid
[    2.170117] usbhid: USB HID core driver
[    2.172277] input: A..... G3 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/input/input5
[    2.172373] hid-generic 0003:E0FF:0002.0001: input,hidraw0: USB HID v1.00 Mouse [A..... G3] on usb-0000:00:1d.0-1.2/input0
[    2.173470] input: A..... G3 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.1/input/input6
[    2.173803] hid-generic 0003:E0FF:0002.0002: input,hiddev0,hidraw1: USB HID v1.00 Keyboard [A..... G3] on usb-0000:00:1d.0-1.2/input1
[    2.195740] ata4: SATA link down (SStatus 0 SControl 300)
[    2.515642] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.526727] ata5.00: ATAPI: HL-DT-ST BDDVDRW CT30F, YT04, max UDMA/133
[    2.530714] ata5.00: configured for UDMA/133
[    2.533769] ata5: exception Emask 0x40 SAct 0x0 SErr 0x80800 action 0x7 t4
[    2.533778] ata5: irq_stat 0x40000001
[    2.533784] ata5: SError: { HostInt 10B8B }
[    2.533796] ata5: hard resetting link
[    2.851545] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.866545] ata5.00: configured for UDMA/133
[    2.867659] ata5: exception Emask 0x40 SAct 0x0 SErr 0x80800 action 0x7 t3
[    2.867662] ata5: irq_stat 0x40000001
[    2.867664] ata5: SError: { HostInt 10B8B }
[    2.867668] ata5: hard resetting link
[    3.187438] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.202518] ata5.00: configured for UDMA/133
[    3.203614] ata5: exception Emask 0x40 SAct 0x0 SErr 0x80800 action 0x7 t2
[    3.203617] ata5: irq_stat 0x40000001
[    3.203619] ata5: SError: { HostInt 10B8B }
[    3.203623] ata5: hard resetting link
[    3.523330] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.538408] ata5.00: configured for UDMA/133
[    3.539525] ata5: exception Emask 0x40 SAct 0x0 SErr 0x80800 action 0x7 t1
[    3.539529] ata5: irq_stat 0x40000001
[    3.539531] ata5: SError: { HostInt 10B8B }
[    3.539534] ata5: hard resetting link

```

Is this helpful to identify the problem? I can post whole log but there are no more important messages about ata5 i think.

Regards

EDIT::

Ok got it : [    2.526727] ata5.00: ATAPI: HL-DT-ST BDDVDRW CT30F, YT04, max UDMA/133

That's damaged dvd drive. Thanks for the help.

---

