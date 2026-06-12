---
title: "Scsi Cd-r"
date: 2005-04-13
forum: Hardware &amp; Laptops
---

### Post by TheWizard on 2005-04-13
Hello,

I've got an old SCSI CD-R I want to use but can't seem to do it... 

I've got a recognized SCSI card and the modules are loaded but I don't know how to continue from here: 

here is the what I think is the relevant information:

dmesg:
```
SCSI subsystem initialized
ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 9
ACPI: PCI interrupt 0000:02:0a.0[A] -> GSI 9 (level, low) -> IRQ 9
   ACARD AEC-671X PCI Ultra/W SCSI-3 Host Adapter: 0 IO:d800, IRQ:9.
         ID:  7  Host Adapter
scsi0 : ACARD AEC-6710/6712/67160 PCI Ultra/W/LVD SCSI-3 Adapter Driver V2.6+ac
ACPI: PCI interrupt 0000:02:0b.0[A] -> GSI 9 (level, low) -> IRQ 9
``` 

lsmod:
```
atp870u                21280  0
scsi_mod              119936  1 atp870u
```

now I don't know if that's relevant so I've pasted it all; /proc/scsi/device_info:

```
'Aashima' 'IMAGERY 2400SP' 0x1
'CHINON' 'CD-ROM CDS-431' 0x1
'CHINON' 'CD-ROM CDS-535' 0x1
'DENON' 'DRD-25X' 0x1
'HITACHI' 'DK312C' 0x1
'HITACHI' 'DK314C' 0x1
'IMS' 'CDD521/10' 0x1
'MAXTOR' 'XT-3280' 0x1
'MAXTOR' 'XT-4380S' 0x1
'MAXTOR' 'MXT-1240S' 0x1
'MAXTOR' 'XT-4170S' 0x1
'MAXTOR' 'XT-8760S' 0x1
'MEDIAVIS' 'RENO CD-ROMX2A' 0x1
'NEC' 'CD-ROM DRIVE:841' 0x1
'PHILIPS' 'PCA80SC' 0x1
'RODIME' 'RO3000S' 0x1
'SUN' 'SENA' 0x1
'SANYO' 'CRD-250S' 0x1
'SEAGATE' 'ST157N' 0x1
'SEAGATE' 'ST296' 0x1
'SEAGATE' 'ST1581' 0x1
'SONY' 'CD-ROM CDU-541' 0x1
'SONY' 'CD-ROM CDU-55S' 0x1
'SONY' 'CD-ROM CDU-561' 0x1
'SONY' 'CD-ROM CDU-8012' 0x1
'SONY' 'SDT-5000' 0x200000
'TANDBERG' 'TDC 3600' 0x1
'TEAC' 'CD-R55S' 0x1
'TEAC' 'CD-ROM' 0x1
'TEAC' 'MT-2ST/45S2-27' 0x1
'HP' 'C1750A' 0x1
'HP' 'C1790A' 0x1
'HP' 'C2500A' 0x1
'MEDIAVIS' 'CDR-H93MV' 0x1
'MICROTEK' 'ScanMaker II' 0x1
'MITSUMI' 'CD-R CR-2201CS' 0x1
'NEC' 'D3856' 0x1
'QUANTUM' 'LPS525S' 0x1
'QUANTUM' 'PD1225S' 0x1
'QUANTUM' 'FIREBALL ST4.3S' 0x1
'RELISYS' 'Scorpio' 0x1
'SANKYO' 'CP525' 0x1
'TEXEL' 'CD-ROM' 0x1
'YAMAHA' 'CDR100' 0x1
'YAMAHA' 'CDR102' 0x1
'YAMAHA' 'CRW8424S' 0x1
'YAMAHA' 'CRW6416S' 0x1
'3PARdata' 'VV' 0x20000
'ADAPTEC' 'AACRAID' 0x2
'ADAPTEC' 'Adaptec 5400S' 0x2
'AFT PRO' '-IX CF' 0x2
'BELKIN' 'USB 2 HS-CF' 0x402
'CANON' 'IPUBJD' 0x40
'CBOX3' 'USB Storage-SMC' 0x402
'CMD' 'CRA-7280' 0x40
'CNSI' 'G7324' 0x40
'CNSi' 'G8324' 0x40
'COMPAQ' 'LOGICAL VOLUME' 0x2
'COMPAQ' 'CR3500' 0x2
'COMPAQ' 'MSA1000' 0x1040
'COMPAQ' 'MSA1000 VOLUME' 0x1040
'COMPAQ' 'HSV110' 0x21000
'DDN' 'SAN DataDirector' 0x40
'DEC' 'HSG80' 0x1040
'DELL' 'PV660F' 0x40
'DELL' 'PV660F   PSEUDO' 0x40
'DELL' 'PSEUDO DEVICE .' 0x40
'DELL' 'PV530F' 0x40
'DELL' 'PERCRAID' 0x2
'DGC' 'RAID' 0x40
'DGC' 'DISK' 0x40
'EMC' 'SYMMETRIX' 0x242
'EMULEX' 'MD21/S2     ESDI' 0x10
'FSC' 'CentricStor' 0x240
'Generic' 'USB SD Reader' 0x402
'Generic' 'USB Storage-SMC' 0x402
'Generic' 'USB Storage-SMC' 0x402
'HITACHI' 'DF400' 0x40
'HITACHI' 'DF500' 0x40
'HITACHI' 'DF600' 0x40
'HP' 'A6189A' 0x240
'HP' 'OPEN-' 0x240
'HP' 'NetRAID-4M' 0x2
'HP' 'HSV100' 0x21000
'HP' 'C1557A' 0x2
'HP' 'C3323-300' 0x20
'IBM' 'AuSaV1S2' 0x2
'IBM' 'ProFibre 4000R' 0x240
'iomega' 'jaz 1GB' 0x21
'IOMEGA' 'Io20S         *F' 0x8
'INSITE' 'Floptical   F*8I' 0x8
'INSITE' 'I325VM' 0x8
'iRiver' 'iFP Mass Driver' 0x80400
'LASOUND' 'CDX7405' 0x90
'MATSHITA' 'PD-1' 0x12
'MATSHITA' 'DMC-LC5' 0x80400
'MATSHITA' 'DMC-LC33' 0x80400
'MATSHITA' 'DMC-LC40' 0x80400
'Medion' 'Flash XL  MMC/SD' 0x2
'MegaRAID' 'LD' 0x2
'MICROP' '4110' 0x20
'MYLEX' 'DACARMRB' 0x20000
'nCipher' 'Fastness Crypto' 0x2
'NAKAMICH' 'MJ-4.8S' 0x12
'NAKAMICH' 'MJ-5.16S' 0x12
'NEC' 'PD-1 ODX654P' 0x12
'NRC' 'MBR-7' 0x12
'NRC' 'MBR-7.4' 0x12
'PIONEER' 'CD-ROM DRM-600' 0x12
'PIONEER' 'CD-ROM DRM-602X' 0x12
'PIONEER' 'CD-ROM DRM-604X' 0x12
'REGAL' 'CDC-4X' 0x90
'SanDisk' 'ImageMate CF-SD1' 0x2
'SEAGATE' 'ST34555N' 0x20
'SEAGATE' 'ST3390N' 0x20
'SGI' 'RAID3' 0x40
'SGI' 'RAID5' 0x40
'SGI' 'TP9100' 0x20000
'SGI' 'Universal Xport' 0x100000
'SMSC' 'USB 2 HS-CF' 0x440
'SONY' 'CD-ROM CDU-8001' 0x4
'SONY' 'TSL' 0x2
'SUN' 'T300' 0x40
'SUN' 'T4' 0x40
'TEXEL' 'CD-ROM' 0x4
'TOSHIBA' 'CDROM' 0x100
'TOSHIBA' 'CD-ROM' 0x100
'USB2.0' 'SMARTMEDIA/XD' 0x402
'WangDAT' 'Model 2600' 0x200000
'WangDAT' 'Model 3200' 0x200000
'WangDAT' 'Model 1300' 0x200000
'XYRATEX' 'RS' 0x240
'Zzyzx' 'RocketStor 500S' 0x40
'Zzyzx' 'RocketStor 2000' 0x40
``` 

also in that dir I have:
"atp870u" directory and "scsi" file; scsi file reads:
```
Attached devices:
``` 
and nothg more.

thanks in advance and with kindest regards, Nitz.

---

### Post by TheWizard on 2005-04-13
got it working: 

after some jumper-trying (I have no manual for the drive) it got recongnized, strage as it's only the device id jumpers I belive...

anyway the dmesg showed:
```
SCSI subsystem initialized
ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 9
ACPI: PCI interrupt 0000:02:0a.0[A] -> GSI 9 (level, low) -> IRQ 9
   ACARD AEC-671X PCI Ultra/W SCSI-3 Host Adapter: 0 IO:d800, IRQ:9.
         ID:  4  SAF     CD-R4012        6.0N
         ID:  7  Host Adapter
scsi0 : ACARD AEC-6710/6712/67160 PCI Ultra/W/LVD SCSI-3 Adapter Driver V2.6+ac
  Vendor: SAF       Model: CD-R4012          Rev: 6.0N
  Type:   CD-ROM                             ANSI SCSI revision: 02
sr0: scsi-1 drive
Attached scsi CD-ROM sr0 at scsi0, channel 0, id 4, lun 0
Attached scsi generic sg0 at scsi0, channel 0, id 4, lun 0,  type 5
``` ]

so I've edited fstab and added the following line:
```
/dev/sr0                        /media/cdrom1   udf,iso9660     ro,user,noauto  0       0
``` 

and created a dir "cdrom1" in /media and limbolic link cdr to it there.

it's ALIVE, it's ALIVE!!!

question: did I do right, in the fstab etc, and dir name and the link or should I do things differently? I only followed reason (from the other lines and dirs and files etc.), Thanks.

---

### Post by alastair on 2005-04-13
Looks OK - but the proof's in that it works for you.

The first post showed no actual devices, just the card. Glad you sorted it out. SCSI can be a pain (still).

---

