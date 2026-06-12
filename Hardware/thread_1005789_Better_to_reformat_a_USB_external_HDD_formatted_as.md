---
title: "Better to reformat a USB external HDD formatted as NTFS?"
date: 2008-12-08
forum: Hardware
---

### Post by Jenske on 2008-12-08
I've recently hooked an Iomega 500 Gb hard disk (USB) to my Ubuntu computer. This HDD is NTFS-formatted.

(By the way: Ubuntu did NOT recognize this device automatically, so I had to manually mount the system (and adjust fstab accordingly))

Would there be a reason to format it (using Gparted) to another system like ext3?
Does this improve security--I seem to remember that ext3 is a very good and stable way of storing data, where other systems are more susceptible to loss.
Does this improve read-write speed?
Does this improve storage capacity significantly?

---

### Post by MarblePanther on 2008-12-08
If you are not going to access that hd from any windows machines, then yes, format it to ext3.

It will be faster and more stable to right and read on a native linux filesystem from a linux machine.

---

