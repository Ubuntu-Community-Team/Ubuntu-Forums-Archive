---
title: "unable to mount cdrom during instalation"
date: 2008-01-17
forum: Hardware &amp; Laptops
---

### Post by mcrae on 2008-01-17
I have just set up new computer: Intel Dual Core E2180 2GHz CPU
MSI P35 NEO2-FIR P35 RAID FW S775 motherboard
2GB DDR2 RAM
I intended to use CDrom only for the installation, therefore I've put an old Asus 50x CDrom. I started the installation with this debian-40r2-i386-CD-1.iso CD (burned from the image) and after the language and keyboard selection, when it tries to mount the cdrom it complains that cannot find it. I tried to go in the console and mount it myself, but I really don't find it in /dev/...the installation also asks for drivers from floppy.
The first attempt was to try usb stick installation. I used a usb card reader (had no normal usb stick). The usb appeared in the boot sequence device list, I selected it as the first boot device, but then I got some message like this:
"Remove cd or any other bootable media and press any key to continue" and that was all - nothing happens after that.
I also tried ubuntu knoppix with the same result. Then I tried to instal winXP and it worked. When I connected to internet I've tried net-boot via goodbye-microsoft.com ... after the reboot, when I choose Debian Installer...I only get a complain that Windows cannot start because it cannot read some file etc. I will now give this way another try - I will reinstall the XP once again on a new primary, active partition in the beginning of the hdd and try again goodbye-microsoft.com ...

Is it anyway possible that the old cdrom device makes the problem...I can bring home newer dvdrom tomorrow...or there is another answer

Thanks in advance!!!

---

### Post by theophile on 2008-01-17
Is the drive ATAPI or SCSI? How is it connected? Do you have any errors in dmesg?

---

### Post by mcrae on 2008-01-18
the solution was pretty simple, although not so obvious:
in the installation Help menu I've found this under SPECIAL BOOT PARAMETERS - VARIOUS HARDWARE:

Force use of generic IDE driver generic.all_generic_ide=1

so one starts the installation like this:


```
boot: install generic.all_generic_ide=1

```

This of course should be combined with the corresponding options in the BIOS, regarding the IDE devices. For me it didn't work if RAID was selected to be IDE; I had to switch it to RAID...but these options can look different depending on your BIOS version.

I hope this can be useful
Good luck!

---

