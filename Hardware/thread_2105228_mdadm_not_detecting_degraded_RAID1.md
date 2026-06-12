---
title: "mdadm not detecting degraded RAID1"
date: 2013-01-15
forum: Hardware
---

### Post by martinweiss on 2013-01-15
I have a degraded RAID1 device (1 disk) from OpenMediaVault. 

I've no problems mounting the disk in OpenMediaVault (Debian). But I can't in Ubuntu. After I install mdadm the RAID device doesn't show up when I do cat /proc/mdstat.

If I reboot the system, Ubuntu won't boot, it just hangs with black screen.

Any help please? Should I install any other packages? The installation of mdadm was without any problems.

I'm running Ubuntu 12.10 64-bit on a Pentium 4.

---

### Post by SaturnusDJ on 2013-01-16
After booting a working Ubuntu (live environment) and attaching the hard disk drive, run:
mdadm --assemble --scan

If no array's show up after running the command, try this one for the raid component:
mdadm --examine /dev/sd*
This will tell you if a valid mdadm superblock is present at the device.

---

### Post by the_marsbar on 2013-01-19
Thanks a lot for your reply!

I did mdadm --assemble --scan, but nothing showed up...

I then did mdadm --examine /dev/sdc and it says Array State : .A (which should mean missing, but active).

I only have one disk in the computer, but surely I should be able to mount a degraded RAID? I'm not sure how to do it. I have searched for an answer, but I couldnt find anything. Quite frustrating...

---

### Post by SaturnusDJ on 2013-01-22
Try this:
```
mdadm --assemble /dev/md0 /dev/sdc
```

Won't work probably.

Here's someone with a similar problem, where using force is the solution: [http://ubuntuforums.org/showthread.php?t=1652976](http://ubuntuforums.org/showthread.php?t=1652976)

Does this work? Otherwise reply with the full output from ```
mdadm --examine /dev/sdc
```

---

### Post by the_marsbar on 2013-01-22
> **SaturnusDJ said:**
> Try this:
```
mdadm --assemble /dev/md0 /dev/sdc
```

Won't work probably.

Actually this DID work :D

Thanks a lot! I've been trying a lot of different things.

---

