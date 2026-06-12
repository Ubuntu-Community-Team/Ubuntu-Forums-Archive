---
title: "RAID5 HDDs won't stay spinned down"
date: 2010-06-18
forum: Hardware
---

### Post by Guybrush333 on 2010-06-18
Hi guys!
I hope i posted this in the right forum cause I'm actually running Ubuntu Server but i think this might be an issue in all varients.

I have the following problem:
I have 4 2TB hdds in a linux software raid 5. Filesystem is ext4. I set the spin-down time of them all with "hdparm -S240" (20 Minutes). And configured the smartd deamon not to spin up the disks for a hdd check.
As far as i can tell they spin down after that time, but even though there's no access to them they spin up, after a while. No idea why though, but as i want the server to run 24/7 i want it to be quiet and energy saving.

The Raid is mounted in /data and the only thing on it are 5 files (its still quite new) no programs or anything.
Only a samba share was created in /data/share/ but I didn'T access that.

in /var/log/messages i only find this:

```

Jun 18 19:22:45 myserver kernel: [ 3627.515141] ata3: hard resetting link
Jun 18 19:22:50 myserver kernel: [ 3632.718031] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jun 18 19:22:50 myserver kernel: [ 3632.722957] ata3.00: configured for UDMA/133
Jun 18 19:22:50 myserver kernel: [ 3632.722977] ata3: EH complete
Jun 18 19:22:59 myserver kernel: [ 3641.509000] ata4: hard resetting link
Jun 18 19:23:04 myserver kernel: [ 3646.471470] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jun 18 19:23:04 myserver kernel: [ 3646.476388] ata4.00: configured for UDMA/133
Jun 18 19:23:04 myserver kernel: [ 3646.476407] ata4: EH complete
Jun 18 19:23:12 myserver kernel: [ 3654.501966] ata5: hard resetting link
Jun 18 19:23:17 myserver kernel: [ 3660.064860] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jun 18 19:23:17 myserver kernel: [ 3660.069209] ata5.00: configured for UDMA/133
Jun 18 19:23:17 myserver kernel: [ 3660.069227] ata5: EH complete
Jun 18 19:23:26 myserver kernel: [ 3668.508180] ata6: hard resetting link
Jun 18 19:23:31 myserver kernel: [ 3673.708289] ata6: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jun 18 19:23:31 myserver kernel: [ 3673.713148] ata6.00: configured for UDMA/133
Jun 18 19:23:31 myserver kernel: [ 3673.713166] ata6: EH complete

```Well and i really don't know what that exectly means or does...
Well it does spin up my disks apparently...

Any ideas?
Please!

---

