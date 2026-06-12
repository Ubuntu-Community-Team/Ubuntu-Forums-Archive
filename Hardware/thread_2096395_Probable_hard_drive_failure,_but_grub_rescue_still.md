---
title: "Probable hard drive failure, but grub rescue still comes up"
date: 2012-12-19
forum: Hardware
---

### Post by CarpKing on 2012-12-19
I have recently been trying to get my long-unused computer up and running.  The first time, it booted successfully, but since then it has not.  Most recently it makes several rapid clicking sounds and pops up a "grub rescue" prompt.  It still boots from USB, but the primary hard drive doesn't show up.  

Does the fact that grub still does something mean the hard drive isn't completely done for?  Before it stopped showing up from the live USB, I ran fsck on it, which fixed some errors but didn't make it bootable.  If it has failed, I plan to partition my other drive (which contains my data) and reinstall on it.

---

### Post by ahallubuntu on 2012-12-19
Stop trying to read anything from the drive and check the drive's  S.M.A.R.T. status before doing anything else.  You can do this from a Ubuntu Live CD if you install GSmartControl - or you can download/burn/boot a copy of the Parted Magic Linux distro which has S.M.A.R.T. control built in ("Disk Health").  Look at the Attributes tab for any Attributes highlighted in red.  Report those here - or use the terminal version "smartctl" and report the results.

If you have more than one pending sector you are almost certainly having serious problems with the drive.  In that case, no point in trying to install anything on it.

It should go without saying that you should have already tried to copy anything off this drive you still wanted to save ASAP.  Failing drives tend to keep getting worse until they become completely inaccessible without expensive equipment to retrieve data from the platters.

---

