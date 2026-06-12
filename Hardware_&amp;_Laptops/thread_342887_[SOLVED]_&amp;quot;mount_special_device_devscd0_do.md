---
title: "[SOLVED] &amp;quot;mount: special device /dev/scd0 does not exist&amp;quot;"
date: 2007-01-20
forum: Hardware &amp; Laptops
---

### Post by vincencollins on 2007-01-20
I have installed Ubuntu 6.10 Edgy Eft on a Sager NP5760-V laptop and I get the following message when I try to mount the internal cd/dvd drive.  

"Unable to mount the selected volume."
"Show more details"
"mount: special device /dev/scd0 does not exist"

I am obviously able to use the live cd to install and the dev directory under the live cd has numerous additional entries.

---

### Post by vincencollins on 2007-01-22
The problem appears to be that ubuntu isn't recognizing the scsi cd/dvd drive.

I don't understand why it is seeing the drive when I boot with the live disk to install but isn't working when booting from the installation.

---

### Post by vincencollins on 2007-04-29
The problem for others that find this is that the ACPI either needs to be turned off by putting acpi=off in the menu.lst or the DSDT needs to be rebuilt.  Look for this line in your dmesg (ACPI: Looking for DSDT ... not found!).  I am actually in the process of recompiling the DSDT for my model laptop but here are the [instructions]("http://gentoo-wiki.com/HOWTO_Fix_Common_ACPI_Problems") to do that for others that might want to get started on your own.

Vincen Collins

---

### Post by D!mon on 2007-05-03
I have the same issue with 7.04; posted the bug here: [https://bugs.launchpad.net/bugs/106698](https://bugs.launchpad.net/bugs/106698)
Maybe you can help to fix this too.
Please post the solution here if you will be able to fix it.

---

### Post by lbarcala on 2007-12-13
I have the same problem. My CD/RW unit worked fine with Dapper Drake. Now I have a clear new Gutsy Gibbon ad the cd does not work.

sudo mount /dev/scd0

mount: special device /dev/scd0 does not exist.

The fstab includes the entry:

/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0

Any solution to the problem?

---

### Post by vincencollins on 2007-12-13
The resolution is to use lilo as the bootloader instead of grub.  This [page]("http://users.bigpond.net.au/hermanzone/p4.html") has all the details on how to configure lilo.

This also applies to 570U which is sold under various brands.

---

### Post by lbarcala on 2007-12-17
Have we only to install lilo? Any specific configuration? I don't know why lilo will solve my problem, but I'll try it.

I don't understand what lilo can do that grub does not to this case. I will put the result to this thread.

Thanks,

---

### Post by lbarcala on 2007-12-18
I have installed lilo into de MBR and the problem persists. I have realized that CDRW unit is not in my Windows Partition also !!! But CD unit was there before installing Ubuntu Gutsy Gibbon !!!
Is it possible that the unit have crashed just after installation? I have installed Gutsy from CD and all was ok but I now cannot boot from CD!!! It seems like the BIOS have lost the information about the CD unit!! Is it possible that Gutsy installation have caused it? I cannot belive that the CD unit or BIOS or some hardware UNIT have crashed just after the Ubuntu installation!

Any idea?

Thanks in advance,

---

### Post by lbarcala on 2008-01-08
Indeed, some days after installing Gutsy Gibbon the CDRW unit has crashed and the BIOS does not detect it. I think it is an unrelated coincidence.

Thanks,

---

