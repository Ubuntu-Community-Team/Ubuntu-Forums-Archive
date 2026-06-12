---
title: "Live CD X Server issue"
date: 2006-02-08
forum: Installation &amp; Upgrades
---

### Post by Jonathan Scholis on 2006-02-08
When trying to boot from the live CD, I get a "Failed to start the X Server" message.  Upon viewing the details I see the following error:

(EE) RADEON(0): [dri] DRIScreenInit failed. Disabling DRI.

I also see some warnings, two of which were interesting:

"'fonts.dir' not found"

"Open APM failed (/dev/apm_bios) (No such file or directory)"

The computer I am behind has the following potentially relevant specs:

Windows XP Home Edition Service Pack 2 (build 2600)
ATI RADEON XPRESS 200 Series [Display adapter]
BIOS: Phoenix Technologies, LTD 3.13 11/15/2005
AMD Sempron 3500+ processor

Any suggestions?  This computer has a software modem, so there isn't much possibility of downloading driver updates while in Linux.

---

### Post by R_MAC on 2006-02-13
I had a similar problem with the LiveCD, not exactly yours, but files and directories missing etc. I had burned the disk image on one drive using CDRW media (didn't want to waste a cd if I didn't like the OS- el cheapo) and booted from primary CDROM drive. When I changed the boot order of the drives and used the secondary CD burner drive, all went as it should and the OS booted with no errors. As I say, not the same but may shed some light.

---

