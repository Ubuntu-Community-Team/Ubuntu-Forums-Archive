---
title: "Testdisk and a Western Digital WD500AAKS"
date: 2009-07-28
forum: Hardware
---

### Post by RamPeij on 2009-07-28
I am running Ubuntu 9.04 with Testdisk and Photorec to try and recovery music files from a Vista HDD.  A Western Digital WD500AAKS 500 GB SATA HDD.   After connecting it to an external HDD kit, I then connect it to the Ubuntu machine.  Ubuntu sees the USB drive, but is unable to mount it.  After reading up in the forums, I learned about "Testdisk" and figured it was worth a try.  Using testdisk I get the following:

TestDisk 6.10, Data Recovery Utility, July 2008
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

  TestDisk is free software, and
comes with ABSOLUTELY NO WARRANTY.

Select a media (use Arrow keys, then press Enter):
Disk /dev/sda - 41 GB / 38 GiB - ATA Maxtor 6E040L0
**Disk /dev/sdb - 2199 GB / 2048 GiB** -
Disk /dev/sdc - 20 GB / 19 GiB - IBM-DPTA -372050

[Proceed ]  [  Quit  ]

Note: Disk capacity must be correctly detected for a successful recovery.
If a disk listed above has incorrect size, check HD jumper settings, BIOS
detection, and install the latest OS patches and disk drivers.

The bolded text is the HDD in question.  As you can see, it is showing up as a 2 TB HDD.

So I proceeded into the "Geometry" section to make the needed changes.
After the changes, the correct HDD size is shown.  I then go back to the "Write MBR" option and after 2 "Y" responses, it says the changes were made and I needed to restart my machine.

Now for the issue.  After the reboot the drive is still not able to be mounted and it comes back as being a 2 TB drive in Testdisk.  Am I missing something?  What other options should I try?

Thank you for your time and patience.

---

