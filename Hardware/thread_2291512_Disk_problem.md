---
title: "Disk problem?"
date: 2015-08-20
forum: Hardware
---

### Post by tommy2k10 on 2015-08-20
I am troubleshooting a computer that won't boot into Windows 8.1.  Ubuntu says the disk is ok, but that the SMART attribute Read Error Rate is 7 figures.  As the description of it (when the mouse is hovered over the top) is if this is a non-zero value, this indicates a problem with either the disk surface or the read/write heads.  
Any recommendations?

---

### Post by Mark Phelps on 2015-08-20
If indeed, the hard disk has either head damage or surface damage, NOTHING you do is going to get it working again.  The only way to repair either of those types of damage is to have the drive repaired -- and that involves sending it to a commercial repair facility, and those generally charge $1000 USD and up, to repair drives because they physically rebuild them in clean room environments.

You're not going to be able to effectively troubleshoot Windows booting problems using Linux utilities; instead, you need Windows boot repair utilities.  You will need to be able to obtain a Win8.1 Installation DVD, boot from that, and run Startup Repair -- probably several times.

The other problem you're going to have trying to use Linux to troubleshoot problems with Win8.1, is that version of Windows enables FastStartup by default (NOT the same as Fast Boot).  This puts the machine, and its drives, into a new form of hibernation whenever you shut down Windows.  That prevents Linux from being able to mount the drive partitions.  Thus, you can't even open the files and folders using Linux.

---

### Post by weatherman2 on 2015-08-20
> **tommy2k10 said:**
> I am troubleshooting a computer that won't boot into Windows 8.1.  Ubuntu says the disk is ok, but that the SMART attribute Read Error Rate is 7 figures.  As the description of it (when the mouse is hovered over the top) is if this is a non-zero value, this indicates a problem with either the disk surface or the read/write heads.  
Any recommendations?

You can run S.M.A.R.T. tests from Ubuntu (or some other Linux boot disk) using GSmartControl.  You can install GSmartControl in a Ubuntu live boot (via Ubuntu Software Center) but you first have to enable the "universe" repository, then must be connected to the internet to download the packages you need.  Or get a Linux distro that has it already installed.  There is a free version of Parted Magic (Linux distro) out there on Major Geeks if you look for it - then you can boot that and use "Disk Health" (GSmartControl) to run the tests.  Run the short S.M.A.R.T. test first - should take only about two minutes.  If that passes, run the extended test, which may take hours, longer for a larger drive.

If Extended S.M.A.R.T. passes? Not sure where you would go from there.  Could be a Windows thing and an ignorable S.M.A.R.T. Attribute.

---

### Post by tommy2k10 on 2015-08-21
Thankyou.
I took your advice and started the SMART tests and ran them overnight.  They both passed, but Windows is still not booting!  I am starting to think it could be a file system problem.  However, what is odd, as mentioned before, is the SMART data gives a non-zero value for Read Error Rate!

---

### Post by tommy2k10 on 2015-08-21
I think I am going to rebuild it from the recovery partition!  Quickest and cheapest way!

---

