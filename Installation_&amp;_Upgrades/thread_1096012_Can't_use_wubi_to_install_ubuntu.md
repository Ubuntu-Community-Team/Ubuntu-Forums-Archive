---
title: "Can't use wubi to install ubuntu"
date: 2009-03-14
forum: Installation &amp; Upgrades
---

### Post by NU_Egypt on 2009-03-14
Hi,
I'm using Vista Enterprise and have used Wubi to install ubuntu. Now i have the option in the start list to choose between windows and ubuntu but whenever i choose ubuntu i can't complete the installation properly. i get busybox and initramfs prompt

Does any body have any idea why could this happen and how to start ubuntu correctly?

Thanks

---

### Post by avtolle on 2009-03-14
There are a few explanations for the difficulty you are having. Prior to installing via Wubi, did you defragment your HDD? A badly fragmented drive will, at least sometimes, cause the problem you are having. You should uninstall Ubuntu, defrag the drive (more than once if using the native Windows tool), then reinstall.

Another potential explanation: have you not cleanly shut Vista down in the past, that is, just became frustrated and turned the power off with Vista running? If so, this may have corrupted your file system. You should, if this is the case, uninstall Ubuntu, run chkdsk -r (this is from memory; check the Wubi Guide for precise instructions), shut Windows down from the Start menu, restart your computer, and then reinstall using Wubi (if this is what you want to do).

Or, this could be an issue with Ubuntu itself; there are many threads about being dropped to Busy Box where installation is done directly to a partition on the HDD. 

I would suggest taking a look at the first two options first, and then looking for other threads on the Busy Box problem if neither is applicable. Good luck.

---

