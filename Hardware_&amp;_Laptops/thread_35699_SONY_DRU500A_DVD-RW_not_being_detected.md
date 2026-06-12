---
title: "SONY DRU500A DVD-RW not being detected"
date: 2005-05-19
forum: Hardware &amp; Laptops
---

### Post by metallikop on 2005-05-19
I'm having a problem loading my IDE DVD-RW drive.  The drive is detected on boot by the BIOS, Windows and the Ubuntu Live CD see it without any problem.  I can boot the Live CD off of it without issue.  The problem is when I boot, hdc isn't being detected, though hdd (SONY CD-RW CRX220E1) on the same chain is being detected.

```
alake@lanfear:/$ dmesg | grep hd
SCSI device sda: 490234752 512-byte hdwr sectors (251000 MB)
SCSI device sda: 490234752 512-byte hdwr sectors (251000 MB)
hdd: SONY CD-RW CRX220E1, ATAPI CD/DVD-ROM drive
hdd: ATAPI 52X CD-ROM CD-R/RW drive, 2048kB Cache
    ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:DMA
hdd: ATAPI 52X CD-ROM CD-R/RW drive, 2048kB Cache
```

```
alake@lanfear:/$ grep -v ^# /etc/modules
sr_mod
ide-cd
ide-disk
ide-generic
lp
sbp2
mousedev
psmouse
nvidia
```

```
alake@lanfear:/$ ls /dev/hd*
/dev/hdd
```

I don't imagine this to be a difficult fix, though it has me completely stumped.  I'd appreciate any help.  Thanks.

---

### Post by dekoi on 2005-05-20
have you tried:
(in terminal)
~$: sudo mount /dev/hdc


that should do it.

---

### Post by metallikop on 2005-06-10
/dev/hdc isn't in my fstab so that won't do much good.

---

