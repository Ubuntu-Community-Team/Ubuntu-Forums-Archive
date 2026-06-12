---
title: "Booting from external scsi drive"
date: 2009-03-01
forum: Installation &amp; Upgrades
---

### Post by lotus49 on 2009-03-01
After a motherboard failure on a machine which booted from an external SCSI disk and then mounted a bunch of drives which formed an LVM VG I moved all the disks to another machine.

For some reason the new machine is making no attempt to boot from the SCSI drive and just complains that there is "No active partition".  I have booted from a live CD and the SCSI disk was recognised as /dev/sda and its contents looked fine (with an active partition /dev/sda1).  The SCSI settings also look fine, correctly listing LUN 1 (the HD) as the boot device.

I set up the original machine a long time (> 2 years) ago and I cannot remember if I had to do anything special to get the system to boot from the SCSI drive.

Does anyone have any suggestions?  The main reason why I don't reinstall is the LVM config is stored on the SCSI drive and I need (or at least would like) to recover the data on the LVM disks.

---

### Post by thtrgremlin on 2009-03-01
Judging from the error meggase, it sounds like the bios it set attempt to boot fprom an external scsi device.

Is Ubuntu installed on that external drive? is grub installed on the scsi drive?

If so, but the bios isn't "seeing" it, use the live cd and 'chroot' to the root of the system on the scsi drive, and run ```
update-grub
``` If the configs are right, but there is something machine specific it is missing (or the like), hopefully that would correct any issue.

Just curious, why not have /boot on an internal disk? I'll guess that the scsi drive is always going to be with the machine, but still.

Also, have you tried using the Live CD to boot the system on the scsi drive? That would give a lot of insight either way.

---

### Post by lotus49 on 2009-03-01
Thank you for your suggestions.  Ubuntu was installed and I had run update-grub but your mention of the BIOS settings made me go back and double check.

I am embarrassed to admit it was a simple matter of changing the BIOS boot settings.  For some reason I had got it into my head that the SCSI BIOS dealt with this but clearly it does not.

My system is now booting fine.

The reason I had an external drive as the boot disk it because it was small and it meant that I could use all the space on the other drives for the LVM VG.

---

