---
title: "Unrecoverable crash with IVTV, Sil 3124 and MD RAID5"
date: 2008-06-01
forum: Hardware
---

### Post by am4c130d on 2008-06-01
Hi,

I have a strange issue on my server.

The server is an Abit IS7 motherboard which has an Intel 865PE northbridge, with a Koutech Sil 3124 based four port SATA controller, a Hauppauge PVR-250 and Netgear/Realtek GigE card.  The system runs MythTV and is my primary backend.

I have four 500G SATA drives on the Sil 3124, configured as RAID5 by mdadm.  I created the RAID on the raw drives themselves, rather than built up partitions etc.  I also have two 250 G SATA drives running from the embedded SATA controller, with three partitions each, running RAID0, and finally I boot everything from an 80G drive hanging off the IDE controller - once this problem is addressed, this drive gets pensioned off to lighter work.

The problem I had is that this was all fine and working well until I added the Koutech controller, and the 500G drives.  At first everything appeared to be fine, but during recording (via MythTV), the system crashed and went in to a boot loop.  The boot loop is normal system POST, GRUB discovers the boot partition and starts to boot, an indication that md1 (the raid5 array on the Koutech) is corrupt, and three or four normal messages until the system would reboot during HW detection.  This condition remains until I remove the Hauppauge card or unplug all the drives from the Koutech card.  Once booted I can reconnect the drives and the system builds fine - until it records again, whereupon it will crash.  What is interesting is that if the system boots correctly, the next message (after detecting HW) is an NTP stop/start message - implying that it is well in to the boot process, however there is no information whatsoever in syslog, it shows normal operation, until the system crashes, then nothing until the system boots correctly.

Once the RAID5 array has been rebuilt, the system will boot fine.

I have played with slots, IRQs, updated the BIOS, upgraded from Gutsy to Hardy all with exactly the same results.  With the exception of the Koutech, the rest of the system has been through every Ubuntu release since Hoary, so I know it's not fundamentally the rest of the system.  However this combination (with the Koutech), has never worked together through Gutsy and Hardy.

Any ideas? 

Thanks

Alan

---

### Post by am4c130d on 2008-06-06
Some progress.  The unrecoverable nature was my fault, the raid was incorrectly configured to use raw devices, not a partition on the disk itself.  Once I partitioned each raid member to use type FD Linux RAID, the system recovered from the crash gracefully.

The issue is that when MythTV access the IVTV card and writes to the RAID array, the system crashes...

Any other ideas?

---

