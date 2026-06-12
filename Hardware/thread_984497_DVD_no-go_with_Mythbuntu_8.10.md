---
title: "DVD no-go with Mythbuntu 8.10"
date: 2008-11-16
forum: Hardware
---

### Post by capnjim on 2008-11-16
I have just upgraded my Mythbuntu box to 8.10. Everything is working (after a little manual work) except my DVD drive no longer auto-mounts new media.

I have found that the drive has changed since the upgrade from being at /dev/scd0 to /dev/sdb. I can manually mount /dev/sdb, and also by path and by label (but not by uuid since the drive does not appear in /dev/disk/by-uuid), however no matter what I try I cannot get it to automatically mount new media.

After mounting, if I try and eject the disk from within Mythbuntu I get a message saying there are no drives to eject. The BIOS startup screen shows the drive as being a SATA drive. I am guessing that for some reason the OS is now seeing the drive as an unmounted SCSI HDD instead of a CD-ROM/DVD drive, which is why it does not auto mount new media?

Can someone advise me on what I need to do to force it to recognise the drive as a CD-ROM/DVD, and ideally mount it back at /dev/scd0?

Thanks in advance.

---

