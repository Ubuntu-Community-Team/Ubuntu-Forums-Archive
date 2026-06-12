---
title: "Raid 1 array cannot be started - feature or bug ?"
date: 2010-09-04
forum: Hardware
---

### Post by jrleighton on 2010-09-04
I have 3 HDDs in my PC.  1 disk hosts the OS - the latest Ubuntu desktop.  The other 2 HDDs are in a software RAID 1 array.
Say one of my RAID disks fails.  I power down and replace the bad disk with a new disk, then power up.
In the disk utility I will want to edit the RAID array to include the new disk and kick off a rebuild.  To edit the array, the array needs to be started, but there is an error (not enough components) so I cannot start the array to rebuild.
This has got to be a bug - no ?  I cannot see that this is a feature.
Anyone else come up with this issue ?

---

### Post by Fafler on 2010-09-04
I have no idea how the gui works, by try starting it in degraded mode.

---

### Post by Joe of loath on 2010-09-04
Is the new disk formatted as a RAID volume?

---

### Post by jrleighton on 2010-09-04
Thanks for the replies....in answer: 
(i) I cannot start the array in degraded mode - that's what I have been trying to do.
(ii) the new HDD is not formatted as a RAID disk.  Any idea how I would do that without including it in a RAID array first ?

Thanks!

---

### Post by jrleighton on 2010-09-05
OK - thanks for the help guys - I now think that this is a hardware issue to do with how I have got the boot order of my disks arranged.  One of my RAID array has GRUB on it, which is causing confusion to the OS.

---

