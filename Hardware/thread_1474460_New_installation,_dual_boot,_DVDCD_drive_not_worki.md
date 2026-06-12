---
title: "New installation, dual boot, DVD/CD drive not working"
date: 2010-05-06
forum: Hardware
---

### Post by gmnorthey on 2010-05-06
I have done quite a bit of research and come to no avail on this issue.

I installed Ubuntu 10.04 (Desktop environment) on my Lenovo IdeaPad Y710.
Driver config is that sda1-3 are my Windows 7 Ultimate platform and sdb1-3 are my Ubuntu 10.04 platform.

My HL-DT-ST DVD-RAM GSA-T20N no longer appears in My Computer and does not appear to be working in Ubuntu (no auto mount and trying to mount in terminal as **mount /dev/cdrom /cdrom** does not work, I also tried doing that as a sudo command).

In Windows 7 it does not appear as a device at all in the My Computer screen, and under Device Manager it is showing up as an unknown device from what I can tell.  I don't seee any other place where it might be showing up.  Attempting to reinstall the device is fruitless.

I have also done a search as apparently there are some errors that affect Windows users with this drive causing the drive to either not show, or show up with a Code 10 or Cod 39 error in windows.  Made registry edits, ran the microsoft automated troubleshooter, and did everything else I could possibly find.

I was able to use the drive until after installing ubuntu.  ALso, when I insert a bootable disc at start up and set the BIOS to load CD/DVD's first, the disc loads, so the physical drive itself seems to be working.

Since the problem seems to be occuring in both Windows and Ubuntu is it possible this is a problem related to GRUB2?

I am running a laptop with 64-bit Intel Core2 Centrino processor, and Windows 7 Ultimate, 2x2GB Ram.  Let me know if any other specs need to be listed.

Please let me know if anyone has any ideas, otherwise I may be forced to reformat and try again.

---

### Post by gmnorthey on 2010-05-07
Anyone have a solution for this?  I still haven't found one.

---

