---
title: "n_sectors mismatch error during boot"
date: 2013-01-28
forum: Hardware
---

### Post by byline on 2013-01-28
There is occasional mention of this problem in various forums, but I have tried various remedies and seen no improvement.

Motherboard: biostar_geforce6100m9
sata driver: sata_nv
drives: have seen this when booting off either a WD Red 2.0TB HD or a Samsung 830 SSD.  Had previously had a Samsung HD160JJ/P installed with NO such problems - strange!

On bootup the output is often of at least one of the following errors:
(1) after the "Verifying DMI Pool Data" line receive the error message "unrecognized file system", then drops to grub rescue
(2) receive an error message such as: "ata3.00: n_sectors mismatch 500118192 != 2251799813685248" followed later by "ata3.00: revalidation failed (errno=-5 or -19)
ata3.00: disabled"
(3) very occasionally see a "model number mismatch"  error

Things I have tried to rectify this situation, without success:
(a) install Ubuntu 12.04 LTS (had been using 10.04 LTS) on a separate partition.  Errors occur regardless of which Ubuntu version I try to boot into.
(b) 3 different SATA cables
(c) plugging into SATA port 2 instead of SATA port 1
(d) add the following to /etc/default/grub (Ubuntu 10.04 and 12.04):
GRUB_CMDLINE_LINUX_DEFAULT="rootdelay=30 splash"
GRUB_CMDLINE_LINUX="sata_nv.swncq=0 libata.force=noncq,1.5G"
- I have tried different rootdelay durations (irrelevant I think, based on when the errors occur) and GRUB_CMDLINE_LINUX command combinations

Once the system is booted, it seems to run quite well.  So it seems to be more of a booting issue and specifically related to grub not receiving accurate info from the SATA device during the booting process.  This is why I tried different SATA cables & ports, but to no avail.

The error that requires most reboots during the booting process is the "n_sectors mismatch" error.
hdparm -i /dev/sda output: LBAsects=500118192

500118192 is always seen within the error message (e.g. n_sectors mismatch 2251799813685248 != 500118192), and consistently the output of hdparm -i is LBAsects=500118192, so is there a way of "forcing" this #LBA sectors during the boot process ?

hdparm -I /dev/sda  shows that 2251799813685248 is actually the # of LBA48  user addressable sectors, so it's not a completely gibberish number

---

### Post by ahallubuntu on 2013-01-28
Any chance there is a newer BIOS available for your Biostar motherboard?  If there is, I'd install it.  That could fix your problem.

---

### Post by byline on 2013-01-29
I've tried that but have run into a hurdle there too.

I downloaded a more recent BIOS from biostar-usa.com and copied it to a floppy using rsync ./filename /media/floppy0/   to ensure a verification occurred after the file was copied to the floppy.  cmp command also does not report any differences between the file on the HD and the one on the floppy.  When I try to use the CMOS utility to update the BIOS though, it reports "file not found"

---

### Post by ahallubuntu on 2013-01-29
Make sure the floppy is formatted in Windows FAT format (not Linux ext).

Also, check the case of the file - it might need to be all UPPERCASE or all lowercase.  Remember, in Windows it doesn't matter, but if you use Linux it could set the case UPPER or lower and the utility is expecting the opposite (whatever Windows would default to).

---

### Post by byline on 2013-01-30
I mounted the floppy using mount -t vfat, so there should be no problem in that regard.  The filename is CU51M119.BS on the biostar-usa.com website, but I'll try converting that all to lowercase and see what happens.  I'll also check file permissions to make sure they're not all set to root.  Not sure if that would make a difference to the CMOS utility during bootup or not, but worth trying.

---

### Post by byline on 2013-01-30
If anyone has a copy of CU51M811.BS (old GeForce 6100 M9 bios) I'd appreciate that !

I was able to perform a BIOS update to CU51M119.BS but booting errors have not improved and now Firefox and various graphical programs are completely locking up - doesn't respond to Ctrl-Alt-F1 or remote log in.  Worse in Ubuntu 10.04 LTS, slightly better in Ubuntu 12.04 LTS

---

### Post by byline on 2013-01-31
Managed to "roll back" the BIOS to version CU51M811 - CU51M811.ZIP available at [www.lejabeach.com/Biostar/6100-939/](www.lejabeach.com/Biostar/6100-939/) if anyone else requires this by the way.  Extracts to CU51M811.BIN actually.

Now back to the original question in Post#1:
- can anyone suggest how to rectify what appears to be SATA communication errors during bootup ?
- is there a way of "forcing" the #LBA sectors to 500118192 during the booting ?

---

