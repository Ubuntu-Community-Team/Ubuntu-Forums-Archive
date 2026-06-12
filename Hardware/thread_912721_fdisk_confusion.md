---
title: "fdisk confusion"
date: 2008-09-07
forum: Hardware
---

### Post by mhowell67 on 2008-09-07
Not sure if this is the right place for this question but anyway;

This is what I see when I run "fdisk -l" on my system.

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x984e984e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4658    37415353+  83  Linux
/dev/sdb2            4659       30401   206780647+   f  W95 Ext'd (LBA)
/dev/sdb5            4659        4863     1646631   82  Linux swap / Solaris
/dev/sdb6   *        4864       11239    51215188+  83  Linux
/dev/sdb7           11240       17615    51215188+  83  Linux
/dev/sdb8           17616       23990    51207156   83  Linux
/dev/sdb9           23991       30401    51496326   83  Linux

What confuses me is sdb2. How can one partition 'overlap' the remaining partitions?  Is this normal?  The partitions were created from windows xp with partition magic.

It doesn't seem to be causing any problems with installations or running kubuntu.

---

### Post by banewman on 2008-09-07
That's the extended partition - that is why it overlaps all the remaining partitions, they're logical partitions in the extended one. :)

---

### Post by mhowell67 on 2008-09-07
> **banewman said:**
> That's the extended partition - that is why it overlaps all the remaining partitions, they're logical partitions in the extended one. :)

Not really sure what that means but I'll go RTFM when I get a chance. I found it bothersome that a "w95" partition seemed to umbrella my linux partitions but apparently it's not hurting anything.

Thanks,

---

