---
title: "USB drives sequence changes every boot"
date: 2006-06-25
forum: Hardware &amp; Laptops
---

### Post by manutremo on 2006-06-25
I have Ubuntu 6.06 installed. I have added several USB drives which I'd like to mount at start-up, in order to make backups from my internal HDs.

I have added entries for all of them in fstab, but i found that the SCSI sequence can change in every reboot.

For example, in one reboot the drives are given /dev/sdg1, /dev/sdh1, /dev/sdm1 and /dev/sdn1... so I put the following entries in fstab

/dev/sdg1     /media/usb1
/dev/sdh1     /media/usb2
/dev/sdm1     /media/usb3
/dev/sdn1     /media/usb4

sudo mount -a mounts them ok.

If I restart, the sequence changes to /dev/sdh1, /dev/sdi1, /dev/sdm1 and /dev/sdn1, and so when the SO tries to mount the entries in fstab, it gives an error.

Also I find that I can't write a script for rsync to perform the backup, as I can't trust the that mount points are always the same.

All the 4 USB drives are connected to the same USB2 card, and I have disabled "Mount removable drives when hot-plugged" in Preferences.

Is there a way to fix the scsi sequence or at least to trust that the mount points will always be the same?

---

