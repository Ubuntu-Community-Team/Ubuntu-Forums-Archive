---
title: "Could use of DVD/DVD software be the cause of hard disk failure (symptoms)"
date: 2007-07-14
forum: Hardware &amp; Laptops
---

### Post by oneiota on 2007-07-14
I've been using Ubuntu (Feisty Fawn) on a Western Digital 250GB SATA hard drive for several months.

Twice now I have had problems with the hard drive that seem to follow directly from an attempt to use the DVD drive.

In first instance, after unsuccessfully trying to watch a DVD, my system failed to boot finding a buffer i/o error on device sda1 - the hard drive (not the dvd drive).  That was resolved after running fcsk.

In the current instance, I attempted to copy a DVD, and noted that the process of copying/preparing the DVD seemed to run for more than a half hour so I left the computer unattended.  Later I found that I could only boot into read mode as root, claiming a hard drive error again.

At the moment, I cannot boot normally and I am not sure what command to run in recovery mode to help things.

If you can help, I would be grateful for suggestions.  One thing I wonder is if the act of copying a DVD causes the hard disk to appear to fail.  It's just a hunch, as it seems the only two times I couldn't boot were immediately following DVD operations.

---

### Post by vanadium on 2007-07-14
My feeling is that your hard drive is at fault. It will sooner or later break down completely. That you have the impression that it is after using DVD software seems logical, as at these moments you are intensively using the drive. I am pretty sure that you just will need to replace the drive to solve your problems. It is fortunate that hard drives are not expensive anymore these days.

---

### Post by oneiota on 2007-07-14
Thanks for your reply.  The drive is still under warranty so I can have it replaced.  Do you think I can do anything to verify that the disk is at fault?

---

### Post by vanadium on 2007-07-14
There are disk testing utilities out there, but I am afraid I can help you specifically. Perhaps you can leave it to your vendor to prove it is not the disk. It si after all with the disk you are having your problems now. (he might blame it on Linux, though!)

---

### Post by oneiota on 2007-07-17
I have a feeling it may not be the hard drive itself and it may indeed be Ubuntu, as I booted into Windows, loading a test disk application mentioned in another thread.  I can see the disk just fine from Windows but when I load the live CD, Linux cannot see the disk at all.  I have a feeling I've messed up an internal state of the drive.

In any case, the supplier has agreed to take it back and take a look at it.  I will see what their diagnosis is.

---

### Post by oneiota on 2007-08-09
For completeness, there perhaps was a disk failure as the supplier has issued me a new one!  Now to focus on reinstalling the OS and applications!

---

### Post by fredj on 2007-08-10
Since this is a sata drive you might like to search for the post 'Is Ubuntu killing your hdd' and read
through that thread. It seems that the present kernels do not power down sda devices properly
and this can shorten the life of a hdd. This is a kernel problem rather than an Ubuntu problem
but there are fixes for it.

---

### Post by ramjet_1953 on 2007-08-10
The latest kernel release has addressed the unmount /  spin down problem.

Even before then, the issue was really irrelevant as it would take you about 20 years to reach the failure point of forced parking, with three shutdowns a day.

The issue was real, but in a way was blown all out of proportion.
What is commonly called FUD.

Regards,
Roger :cool:

---

