---
title: "Installation problem: Doesn't recognize HDD"
date: 2009-09-22
forum: Installation &amp; Upgrades
---

### Post by DSKalfelan on 2009-09-22
Hi all,
 
first of all, I'm completely new to anything Ubuntu or Linux in general, and I'd appreciate any help (the more detailed and fool proof the better) this great community could provide me.
 
Now, to the matter:
 
I have a brand new PC with the following specs:
 
- MSI G31M3 V2 (aka Foxconn -moar like Fauxconn-)
- Intel Pentium 64 Dual Core 2.5 ghz L2: 2mb 45nm
- OCZ DDR2 2GB
- Western Digital Blue Caviar WD3200AAJS 320gb
 
The HDD is clean, no partitions, nothing.
 
When I try installing Hardy or Jaunty from the Live CD, the visual installation progresses to step 4, where it should display the HDD to select and create the partitions for the install.
 
That doesn't happen. At all. The HDD is not recognized.
 
Now, I have read this thread: [http://ubuntuforums.org/showthread.php?t=869249](http://ubuntuforums.org/showthread.php?t=869249)
I wondered if the ACPI had something to do with Ubuntu not recognizing my hard-drive. But from the Live CD I cant do the modifications that are suggested at the thread.
 
The curious thing: I have just finished installing an old ver. 6.06 on it, and it seems to run fine. The thing is, I want to have a supported LTS, or at least Jaunty working, since this is for a school and we're heading to a massive migration from Windows to Linux.
 
¿Does anyone have any ideas on how to work this around? I'm open to anything at this point.
 
Thanks a lot,
 
Kal.

EDIT: *ACPI instead of APCI.

---

### Post by dstew on 2009-09-22
It may be that the Linux kernel on the live CD, with its associated modules, is not recognizing your hard disk. Try the [Alternate Install CD]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate"). Sometimes it works when the Live CD will not. It uses a text-based interface to do the installation.

---

