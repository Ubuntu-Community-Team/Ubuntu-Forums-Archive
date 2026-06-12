---
title: "Weird problem mounting an USB Pen Drive..."
date: 2010-08-01
forum: Hardware
---

### Post by asbesto on 2010-08-01
Hi,

just purchased an HP 8 GB Pen Drive,

I plugged on my 10.04 Ubuntu system, created a new fresh ext3 partition with fdisk, created the filesystem structure with mkfs.ext3... no errors at all. Sync, et voila'

when plugging the pendrive I obtain only this:

```

Unable to mount 8.5 GB Filesystem
Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sdc1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

In dmesg I have:

```

[353447.286991] scsi14 : SCSI emulation for USB Mass Storage devices
[353447.287302] usb-storage: device found at 14
[353447.287307] usb-storage: waiting for device to settle before scanning
[353452.284170] usb-storage: device scan complete
[353452.284898] scsi 14:0:0:0: Direct-Access     Generic  Flash Disk       8.00 PQ: 0 ANSI: 2
[353452.288060] sd 14:0:0:0: Attached scsi generic sg3 type 0
[353452.289257] sd 14:0:0:0: [sdc] 16547840 512-byte logical blocks: (8.47 GB/7.89 GiB)
[353452.289751] sd 14:0:0:0: [sdc] Write Protect is off
[353452.289756] sd 14:0:0:0: [sdc] Mode Sense: 03 00 00 00
[353452.289759] sd 14:0:0:0: [sdc] Assuming drive cache: write through
[353452.291867] sd 14:0:0:0: [sdc] Assuming drive cache: write through
[353452.291873]  sdc: sdc1
[353452.576863] sd 14:0:0:0: [sdc] Assuming drive cache: write through
[353452.576871] sd 14:0:0:0: [sdc] Attached SCSI removable disk
[353453.042328] JBD: no valid journal superblock found
[353453.042335] EXT3-fs: error loading journal.

```


I checked the pendrive with badblocks: no errors at all! 

Someone told me about some "active pens" with winblow$ software in it, pens that has to be turned "passive" because they have some sort of hidden data in them.

Can someone help me? The only way I can use this damn pen is formatting it in VFAT, and that's very annoying.

P.S. I have the same error on other Ubuntu versions, and I have no problems with other pendrives I have.

---

### Post by IcarusR on 2010-08-01
Try running... 

```
fsck.ext3
```

Check out the manual page first...

```
man fsck.ext3
```

Possibly use b option ?

---

### Post by asbesto on 2010-08-02
Yes I've tried this, without result.

The news is that badblocks gave me errors on the usb key.

So I returned the key back to the seller, and now I have a samsung 8Gb usb key.

As before, i created an ext3 partition on it.

I plugged the key, and I have THE SAME ERROR AS BEFORE!!!!!

](*,)

What I'm missing? Are 8Gb keys now unusable under Linux?!?!?

---

