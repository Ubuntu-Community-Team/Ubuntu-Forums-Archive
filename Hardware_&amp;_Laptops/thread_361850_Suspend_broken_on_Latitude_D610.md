---
title: "Suspend broken on Latitude D610"
date: 2007-02-14
forum: Hardware &amp; Laptops
---

### Post by Kensey on 2007-02-14
I have a latitude D610 with the Intel GMA915 graphics chipset.  Under Dapper, suspend and hibernate both worked fine.  Since I upgraded to Edgy and enabled aiglx, when I suspend, the laptop won't resume.  The hard drive spins up and the CD-ROM clicks, but the video never comes back and apparently neither does the network (wired or wireless).  Various guides have mentioned kernel boot options and acpi-support options; currently mine are set as follows:

In /boot/grub/menu.lst:

# kopt=root=UUID=d3554a6a-4591-4537-a05c-fb8282bb8c36 ro acpi_sleep=s3_bios

In /etc/default/acpi-support:

ACPI_SLEEP=true
ACPI_SLEEP_MODE=mem
MODULES=""
MODULES_WHITELIST=""
SAVE_VBE_STATE=false
POST_VIDEO=true
# SAVE_VIDEO_PCI_STATE=true
USE_DPMS=true
# DOUBLE_CONSOLE_SWITCH=true

I notice that in the dpkg-old version of the acpi-support file, the ACPI_SLEEP line is commented out, but the ACPI_SLEEP_MODE line is not.  Apart from that, the options are set identically.  I don't understand how I was able to suspend if ACPI_SLEEP was commented out -- is there a non-ACPI method of suspending the laptop?  Do I want to comment out that line in the active acpi-support file, or should I leave it enabled and do something else to fix suspend?

---

