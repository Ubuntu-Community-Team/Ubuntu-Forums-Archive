---
title: "scsi scannet issue"
date: 2007-12-29
forum: Hardware &amp; Laptops
---

### Post by wilstar on 2007-12-29
Hi everybody,
i have one scsi scanner Agfa snapscan e310 with scsi card adaptec 2904. My pc is intel core 2 duo on asus mb p5k se with 2 sata hd and 1 sata dvd-rw. Ubuntu 7.10 64 bit.
i have to boot my pc with scanner on to use it.
i installed scsiadd but it doesn't work.
This is the output of the command:

```
scsiadd -s
could not add device 0 0 2 0 : Invalid argument
could not add device 0 0 3 0 : Invalid argument
could not add device 0 0 4 0 : Invalid argument
could not add device 0 0 5 0 : Invalid argument
could not add device 0 0 6 0 : Invalid argument
could not add device 0 0 7 0 : Invalid argument
could not add device 0 0 8 0 : Invalid argument
Attached devices:
Host: scsi0 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: MAXTOR STM316081 Rev: 3.AA
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi1 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: Maxtor 6L200M0   Rev: BANC
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi3 Channel: 00 Id: 00 Lun: 00
  Vendor: TSSTcorp Model: CDDVDW SH-S203P  Rev: SB00
  Type:   CD-ROM                           ANSI  SCSI revision: 05

```

Thi is the output when scanner works properly (boot linux with it on):

```
scanimage -L
device `snapscan:/dev/sg3' is a AGFA SNAPSCAN 310 flatbed scanner
```

```
sane-find-scanner 

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

found SCSI scanner "AGFA SNAPSCAN 310 1.20" at /dev/sg3
  # Your SCSI scanner was detected. It may or may not be supported by SANE. Try
  # scanimage -L and read the backend's manpage.
```

```
scsiadd -p
Attached devices:
Host: scsi0 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: MAXTOR STM316081 Rev: 3.AA
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi1 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: Maxtor 6L200M0   Rev: BANC
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi3 Channel: 00 Id: 00 Lun: 00
  Vendor: TSSTcorp Model: CDDVDW SH-S203P  Rev: SB00
  Type:   CD-ROM                           ANSI  SCSI revision: 05
Host: scsi2 Channel: 00 Id: 05 Lun: 00
  Vendor: AGFA     Model: SNAPSCAN 310     Rev: 1.20
  Type:   Scanner                          ANSI  SCSI revision: 02

```

Sometimes Host: scsi is number 2, like this one. Sometimes it has number 0 or number 4.

The hardware ID scsi (on the rear of the scanner machine) is set to 5.

Thanks for your interesting.

wilstar

---

