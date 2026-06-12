---
title: "Re-scanning SCSI-like devices?"
date: 2011-06-28
forum: Hardware
---

### Post by hbrednek on 2011-06-28
I have an uncommon situation involving an Ubuntu machine (10.04) and a SCSI-like device connected via fibre channel.  The connected device is removable and can have power applied to or removed from it separate from the Ubuntu machine and it can have either or both of its two disk-like devices (which typically show up as /dev/sdc and /dev/sdd) present or removed.  This can occur at any time.

When using Ubuntu 8.04, applying power to the device (while Ubuntu was running) caused, after a few seconds, the OS to detect the two devices as /dev/sdc and /dev/sdd, bringing up the same dialog box that would appear when inserting a USB device.  And, when power was cycled on the SCSI-like device, the same thing would occur.  All without having to reboot Ubuntu in order to rescan the device; somehow Ubuntu just figured it out and did the right thing.

However, in migrating to Ubuntu 10.04, this behavior is no longer observed.  If, for example, if the Ubuntu machine has completed booting and is in a quiescent state, applying power to the SCSI-like device does not cause Ubuntu 10.04 to recognize that a new device is available like version 8.04 did in the past.

This causes us to have to reboot the Ubuntu machine in hopes that on reboot it will detect the device.  Usually this is successful, but it seems like a really big hammer for a small problem that didn't even exist in 8.04.  Is there a way to force the OS to rescan the devices like it does on bootup?

Note:  I have tried rescan_scsi_bus.sh with no apparent effect, as well as 

echo “- – -” > /sys/class/scsi_host/host0/scan

all with no success.  Is there a way to cause the kernel device selection logic to be re-executed without having to reboot?  In this case, even if it takes the machine down for a few seconds it would be an acceptable workaround.

---

