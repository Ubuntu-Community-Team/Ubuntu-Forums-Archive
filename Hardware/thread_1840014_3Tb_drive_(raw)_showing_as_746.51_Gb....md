---
title: "3Tb drive (raw) showing as 746.51 Gb..."
date: 2011-09-06
forum: Hardware
---

### Post by Moozillaaa on 2011-09-06
Title says it all; it's a new drive, and all that shows is 746 Gb HDD space.

Any ideas about how to proceed here? Like maybe go ahead and format, with disk label assignment, and see if the rest of HDD space shows up?

---

### Post by YesWeCan on 2011-09-06
It'll probably be a GPT formatted disk.
What exactly is showing it as 747GB?

Try sudo parted -l

---

### Post by srs5694 on 2011-09-06
This is a common problem when something in the hardware or software chain has a 32-bit limitation on sector pointers. Basically, the 32-bit limitation equates to 2 TiB (that is, about 2.2 TB). When this value is exceeded, one possible symptom is that the value wraps around and starts counting from 0 again, like a car's odometer. Thus, a 3 TB disk ends up looking like it's actually something on the order of 800 GB (745 GiB) in size.

There have been several posts about this type of problem in the past on this forum. The usual culprit is a USB drive enclosure that has a 32-bit limitation. I've also heard of Windows drivers with such a limitation, although that only affects Windows. I've never heard of this problem showing up in Linux with internal drives, but it's theoretically possible.

If you're using an external USB enclosure or adapter, the only solution I've heard of that works is to replace it with another model that doesn't have this limitation. If you need more advice, please post more details, such as how you're connecting the disk to the computer.

In any event, attempting to partition the disk in this state is likely to create problems. At best, you'll be able to safely use the amount of space that the partitioning software says is available but no more. At worst, you'll create something that's inconsistent and that will result in data corruption sooner or later.

---

