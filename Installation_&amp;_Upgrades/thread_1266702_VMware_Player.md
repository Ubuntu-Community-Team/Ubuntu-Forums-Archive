---
title: "VMware Player"
date: 2009-09-14
forum: Installation &amp; Upgrades
---

### Post by kbraghu on 2009-09-14
Hi All,

After 7 years I am started back to using Linux. I installed Vista and Ubuntu Linux in the same laptop(Duel Boot). Is it possible to access Ubuntu Linux from Vista using VMware. 

Please let me know anyother application do this job.

Regards,
R

---

### Post by kbraghu on 2009-09-15
Any Help ..................

Regards,
R

---

### Post by Simian Man on 2009-09-15
> **kbraghu said:**
> 
After 7 years I am started back to using Linux. I installed Vista and Ubuntu Linux in the same laptop(Duel Boot).
Is a duel boot where two OSs battle for control of a hard drive??

> **kbraghu said:**
> Is it possible to access Ubuntu Linux from Vista using VMware.

No.  VMware is for running instances of other OSs which run on fake hardware under your installed system, not for running OSs that are actually installed on your computer.

You can install ext3 and ext2 filesystem drivers for Windows [from here]("http://www.fs-driver.org/").  That will allow you to read your Linux formatted partitions from within Windows.

---

### Post by lukeiamyourfather on 2009-09-15
Yes and no. If all you want to do is access files on your Linux partition while running Windows use an installable file system. That will allow you to mount the Linux partition in Windows as if it were a native disk. This one works for ext2 and ext3 partitions.

[http://www.fs-driver.org/](http://www.fs-driver.org/)

If you want to run Linux applications inside of Windows there's virtualization like VirtualBox, environments like Cygwin, and other options. However you wouldn't be able to use your Linux partition for the virtual machine disk and for actually booting Ubuntu. If there is a way I'm not exactly sure how that would work since the hardware and drivers for each would be completely different. Cheers!

EDIT: Simian Man beat me to it.

---

### Post by Simian Man on 2009-09-15
> **lukeiamyourfather said:**
> 
EDIT: Simian Man beat me to it.

Well you explained better :).

---

