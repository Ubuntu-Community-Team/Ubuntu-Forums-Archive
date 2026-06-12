---
title: "Ubuntu labels my CD drive as &quot;Floppy Drive&quot; and won't read it."
date: 2010-08-28
forum: Hardware
---

### Post by routtj on 2010-08-28
Ubuntu 10.04.1 (x86) mislabels my CD drive as "Floppy Drive," and won't read from it. I installed Ubuntu via Live CD, so I know it's not a hardware defect. Any help would be greatly appreciated.

ASRock PT880 motherboard
Sony CRX217E CD-R/RW drive (IDE)

Relevant output from lshw:
```

           *-cdrom
                description: CD-R/CD-RW writer
                physical id: 1
                bus info: scsi@3:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                capabilities: audio cd-r cd-rw
                configuration: status=open
```

---

### Post by lidex on 2010-08-29
Have you tried disabling floppy drive in bios?

---

### Post by varunendra on 2010-08-30
> **lidex said:**
> Have you tried disabling floppy drive in bios?
+1

If it doesn't help, put a cd in the drive then post outputs of the following commands:
```
cat /etc/fstab
```
and
```
mount
```

---

