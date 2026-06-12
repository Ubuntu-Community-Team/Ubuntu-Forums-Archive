---
title: "SmartCTL Support For SATA?"
date: 2005-11-27
forum: Hardware &amp; Laptops
---

### Post by SuSUntu on 2005-11-27
I wanted to use "smartctl" to monitor my drives. 

However, when issuing "sudo smartctl -i /dev/sdb", smartctl reports that the "Device does not support SMART".

Both my SATA drives:

WDC WD360GD-00FN (Raptor)
SAMSUNG SP1614C

do support SMART. Running "hdparm -I" for each of those devices indicates that all SMART features are available and enabled. 

I did find some info about the "libata" SCSI driver needing to be patched in order for smartctl to work with SATA:

[http://smartmontools.sourceforge.net/#testinghelp](http://smartmontools.sourceforge.net/#testinghelp)
[http://freshmeat.net/projects/hdparm/](http://freshmeat.net/projects/hdparm/)

but, according to the info in the second link, libata is already patched if "hdparm -I" works.

Any ideas how to get smartctl (SMART monitoring) to work with these drives?

Thank you.

--------------
Additional info:
- SMART is enabled in the BIOS
- SMART works with these drives in Windows XP Pro
- smartctl under Ubuntu DOES work with the PATA drive in the same PC

---

### Post by SuSUntu on 2005-11-28
Update:
--------------------
Well, I was on the right track with libata. I went back and read the first link from my original post, and had I read more carefully the first time, I wouldn't have needed to post my original query. From the link:

> 
Note: ... With a SATA disk driven by a libata driver, smartmontools can now be used by specifying both the device type 'ata' and the SCSI device corresponding to this disk, for example, smartctl -i -d ata /dev/sda. The patch is still under development and it is probably best to make sure that the disk is idle before trying smartmontools.


I neglected to provide the "-d ata" option in my commands, and therefore was getting the results I posted. If the option is included, "smartctl" works in Ubuntu 5.10, and full output is available.

"Smartctl", however does not work in my Centos 4.x install. That, combined with ioctl() error messages issued from "hdparm" in Centos when run against SATA drives, leads me to conclude that the Centos 4.x kernel I'm running doesn't have the patched libata driver. I'm sure someone with more knowledge knows a command to definitively / accurately determine whether the patch is included, but it escapes me just now.

Conclusion:

- "smartctl" does work in Ubuntu 5.10 (patched / up-to-date libata driver)
by using the "-d ata" option;

- "smartctl" doesn't work in OSs with unpatched libata drivers.

Simple enough.

Thanks.

---

