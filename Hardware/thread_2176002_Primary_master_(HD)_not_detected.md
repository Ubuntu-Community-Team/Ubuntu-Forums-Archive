---
title: "Primary master (HD) not detected"
date: 2013-09-22
forum: Hardware
---

### Post by Macamba on 2013-09-22
Hello,

Today I had to reboot my system and while booting I noticed the slowness of the booting process. In the end it complained it could not find the HD. It stopped with the following message
```

Error: no such device 848 [...etc...] 1f5c
Grub rescue

```

I then put my rescue DVD with Live Ubuntu in the CDRom drive, and found out I only had one HD, the one with only data on it. The one with my bootloader and OS'es was lost. Next I went to the shop, came back to try to rescue my system, and I had my normal Grbub bootloader again. 

Only within six months I had to replace the partition with my home directory as it was riddled with bad blocks. I cleaned out another partition, and copied all my files and directories to that new partition. Anyway, you would think the harddisk is suspect. Should I buy myself an new HD (and Windows OS, sigh) and copy everything to the new HD?

Macamba

---

### Post by oldfred on 2013-09-22
Do you regularly run chkdsk on all NTFS partitions. Ubuntu will run fsck on every 40 to 60 reboots.

What does Smart data show. You can see it from Disks or Disk Utility, click on drive. All I know is passed is good and anything else is not. But it can run a variety of tests. Growing number of bad blocks usually is a bad sign, but just a few is not abnormal.

---

### Post by Macamba on 2013-09-23
Looking at the 'Disk Utility' the SMART Status gives a 'Disk has a few bad sectors'. Pressing the 'SMART Data' opened a window with problems in:
[COLOR="#FF0000"][LIST]
[*]Reallocated Sector Count (Normalized/Worst 96, Threshold 10, Value 182 sectors)
[*]Current Pending Sector Count (Normalized/Worst 87, Threshold 0, Value 529 sectors)
[/LIST][/COLOR]

The 'Disk Utility' was looking at the HD with the Windows and Linux partitions. Selecting the volumes with the root partition and so on did not alter the status of the 'SMART Data'. 

Am I correct in concluding my HD is slowly dying?

---

### Post by Macamba on 2013-09-23
I also performed a CHKDSK on the OS partition of Windows and found two damaged clusters. So, should I conclude my HD is dying?

---

### Post by oldfred on 2013-09-23
If it says passed it should still be a working drive. But is starting to go. It could last years or fail in 5 minutes.
And even good drives something crash unexpectedly. Good backups are the only solution. 

I just looked at my drives. Two passed and have no issues. One 7 year old drive shows one bad sector but still says passed. Once one of my drives gets past about 3 years (no matter what warrantee is)  it is demoted to less important activity, so data may be on-line, but is also backed up somewhere else also. And I have had a one year old drive totally fail.

---

### Post by Macamba on 2013-09-26
Thanks. So I better look for a new HD (and what makes it more expensive Windows 7).

---

