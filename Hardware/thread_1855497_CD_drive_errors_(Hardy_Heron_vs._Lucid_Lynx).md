---
title: "CD drive errors (Hardy Heron vs. Lucid Lynx)"
date: 2011-10-06
forum: Hardware
---

### Post by Chris7 on 2011-10-06
Hello,

I have installed Ubuntu 8.04 (Hardy Heron) and Ubuntu 10.04.3 (Lucid Lynx) on the same PC in parallel.

While I have no problems accessing different CDs/DVDs under 8.04, I do have problems with some of them under 10.04, for example:

[LIST=1]
[*]Inserting an audio CD in the tray gives me a repeating block of error messages:```

sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current]
sr 0:0:0:0: [sr0] Add. Sense: Illegal mode for this track
sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
end_request: I/O error, dev sr0, sector 0
```
[*]Trying to ripp this audio CD results in errors for some of the tracks.
cdparanoia:
```
scsi_read error: sector=40033 length=27 retry=0
Sense key: 3 ASC: 11 ASCQ:0
Transport error: Medium reading data from medium
System error: Input/output error
```and even an abort:```

scsi_read error: sector=185476 length=13 retry=1
                 Sense key: 2 ASC: 4 ASCQ: 1
                 Transport error: Device not ready
                 System error: No medium found
```
[*]Inserting a data DVD-RW that has been burned under 8.04 works fine.
[*]Burning this DVD-RW under 10.04 and inserting it then results in similar error messages as (1):```

sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current]
sr 0:0:0:0: [sr0] Add. Sense: End of user area encountered on this track
sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 23 05 3e 00 00 02 00
end_request: I/O error, dev sr0, sector 9180408
```
[/LIST]
 10.04 kernel is 2.6.32-34-generic, the drive uses the PATA driver pata_atiixp.

```
  *-cdrom
       description: DVD writer
       product: DVD DD DW1640
       vendor: BENQ
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: BSHB
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 status=ready

```I browsed this forum and although I've found users with similar problems, the solutions given there (if any) couldn't solve my problem so far. :(

Any ideas?

Thanks in advance.

---

### Post by Chris7 on 2011-10-28
Is there really no one who could advise what to do or check next?

I think it would already help to know if this could be an Ubuntu configuration (application?) problem or rather a kernel driver problem.

---

