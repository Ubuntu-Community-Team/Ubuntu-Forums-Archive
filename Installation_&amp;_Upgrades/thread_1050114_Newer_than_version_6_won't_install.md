---
title: "Newer than version 6 won't install"
date: 2009-01-25
forum: Installation &amp; Upgrades
---

### Post by doglover56 on 2009-01-25
Hello. I can install Ubuntu 6 but not Ubuntu 7 or 8. The problem appears to be dealing with the hard drive and hda vs sda. Same issues with xUbuntu

I have an older Dell 4100 with a P3 processor and two IDE hard drives. On the main first drive I have 3 primary partitions and 1 extended partition with many (too many?) logical partitions. I started this effort with logical partitions hda5-hda17.

Ubuntu 6 calls the drive hda, and will create and format and install the various partitions hda18 (swap), 19 (root), 20 (home) just fine. 

Ubuntu 7 and 8 calls the drive sda, which I see from prior posts is a kernel change. I can create partitions sda18-20 both with the partitioner and with cfdisk, no problem. 

But neither with the partitioner nor with the terminal can I format these partitions. Both crash with errors stating cannot format.

I also notice in the partitioner that preceeding partitions sda 16 and 17 are marked with exclamation points, and the partitioner will not read the filesystems. This is only with (x)Ubuntu 7 and 8, the partitions are fine with (x)Ubuntu 6, or Knoppix, or DSL, or windows. 

So, anyone understand what is going on? I guess I can just stick with Ubuntu or Xubuntu (same issues) version 6, and forget about newer versions unless there is a fix. 

Thanks in advance.
Doglover

---

### Post by oldos2er on 2009-01-25
Which file system are you using to format?

---

### Post by doglover56 on 2009-01-25
I was using both the partitioner and the command line to try to create ext3 filesystems, but neither would work with Ubuntu 7 or 8.

---

### Post by lswb on 2009-01-25
The newer disk drivers that use the sdxx device names are based on the SCSI disk drivers. SCSI has always had a limit of 16 device nodes per SCSI channel or bus. As I understand it, the host system is one node, so that leaves 15 partitions available per disk. My terminology may not be completely correct here but that is the basic idea.

I have read that there is a way to force loading of the older style drivers but don't know the details. It possibly would require adding modules to the initram.img.

---

### Post by doglover56 on 2009-01-26
OK, I wondered about a partition limit. When I googled that question earlier it said 24 partitions, but maybe that was IDE not SCSI. If there is a 15 drive limit, then how come cfdisk happily makes the partitions? Does it not use the same drivers that the formatting program would use?
Thanks,
IMF

---

### Post by lswb on 2009-01-26
I don't know enough to give a precise answer to that question, but it is certainly possible that different drivers are used. The formatting program doesn't really need to "know" if the disk will subsequently be accessed with the older IDE drivers or the current SCSI emulation drivers.

---

