---
title: "No boot on Compaq Presario 5000"
date: 2005-04-21
forum: Hardware &amp; Laptops
---

### Post by hpxchan on 2005-04-21
Hi,

I'm having some install issues with Ubuntu Hoary 5.04 and my Compaq Presario 5000 (Intel Celeron Coppermine 667Mhz, 192MB archaic RAM, 15GB IDE hard drive, standard Realtek NIC clone).

Install with the CD (using standard options) goes without a hitch. After the first reboot, when the machine boots up for the first time under the new OS, I see package names scrolling by for thirty minutes or so, followed by a blank screen with a single underscore (cursor?) at the top-left corner of the page.

This CD worked perfectly with another, considerably newer machine, so I know it is not corrupted or anything.

Any ideas?

Chandler

---

### Post by codejunkie on 2005-04-21
I have had tons of problems with my compaq and linux any distro not just ubuntu i think alot of the errors are power management issues in the bios. 
using the (**linux acpi=off**) for the install disk and the (**live acpi=off**) for the live cd options worked for me. if that does'nt work it could be a grub issue if your dual booting windows and linux make sure you install grub to the bootsector of the primary hard disk.

---

### Post by hpxchan on 2005-04-21
Considering that my computer could finish the part of the installation that is run off of the CD, not to mention make some pretty significant progress in the second part (which is run off of the local hard disk), I had my doubts about ACPI being the problem - it would seem to me that, if I were having problems with ACPI, I would have trouble with the CD, too.

Nevertheless, I tried a reinstall with acpi=off, to no avail. That same white underscore has been populating an otherwise pitch-black monitor screen for about an hour now.

Chandler

---

### Post by lorap on 2005-04-22
hi friends.
i've installed and runned on my hp-compaq nx9010 as well warty as hoary.
try change installation cd,probably your cd reader can't just read it well.
it's just impossible hoary wouldn't run on your machine.
have a nice day.
pavel

---

### Post by codejunkie on 2005-04-24
[QUOTE=hpxchan]Considering that my computer could finish the part of the installation that is run off of the CD, not to mention make some pretty significant progress in the second part (which is run off of the local hard disk), I had my doubts about ACPI being the problem - it would seem to me that, if I were having problems with ACPI, I would have trouble with the CD, too.

Nevertheless, I tried a reinstall with acpi=off, to no avail. That same white underscore has been populating an otherwise pitch-black monitor screen for about an hour now.

Chandler[/QUOTE]
the reason i mentoned the linux acpi=off is my compaq would finish the install and start loading linux and freak at starting hotplug subsystem that worked on mine if yours completes the install but still freezes it could also be lack of memory gnome and kde are pretty big desktop enviorments try using fluxbox or xfce.

---

