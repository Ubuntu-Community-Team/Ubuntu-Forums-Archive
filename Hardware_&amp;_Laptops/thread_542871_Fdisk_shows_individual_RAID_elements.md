---
title: "Fdisk shows individual RAID elements"
date: 2007-09-04
forum: Hardware &amp; Laptops
---

### Post by fowie on 2007-09-04
I am running ubuntu (Dapper) successfully on an HP Netserver LH4r (had to use acpi=off and noapic to get it to book and install).  I am using hardware SCSI to create two RAID5 arrays.  The arrayed drives show up correctly as /dev/sda and /dev/sdb, but I also get a few anomaly drives showing up.  Sometimes on boot I see /dev/sdc thorugh /dev/sdj, sometimes just /dev/sdc and /dev/sdd and the sizes they are reported as having (18GB) makes me believe they are individual elements of my RAID arrays (I also think this because fdisk says their partition types are Linux RAID which is what I formatted my two hardware RAID arrays as).  Why would these show up?  It hasn't caused any problems as long as I don't format or mount those mystery drives, but now that I've got a SATA array in the mix, they SATA drives show up with different drive letters on every reboot, which subsequently destroyed my LVM that I had installed on the SATA array.  Any  help on how to get these drives to stop showing up (hopefully before I recreate the LVM) would be very appreciated.

(Side note.  The LVM failed because the uuid for one of the sata drives is no longer correct, trying to use pvcreate tells me that it ignores one of the drives I need to set up as part of the LVM, so any help with that would be great also)

---

