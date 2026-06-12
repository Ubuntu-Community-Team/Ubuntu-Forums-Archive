---
title: "No common CD-ROM drive detected."
date: 2005-06-18
forum: Hardware &amp; Laptops
---

### Post by phate on 2005-06-18
Hi,

I just bought an Acer Travelmate 4150, and I wanted to install Ubuntu on it.  Problem is, when I go to either install or use the Live cd, it cannot find my cd-rom drive during the hardware detection process.

I am able to get into the original menu, choose my language, and keyboard.  When it starts detecting the hardware, a message pops up telling me: "No common CD-ROM drive was detected"  I then have the option to load the drivers from a floppy (my laptop has NO floppy drive) or choose manually.  I have tried most of the options, but the cd-rom detection always fails.

I found the thread: "http://ubuntuforums.org/archive/index.php/t-4447.html", but it seems the people who had the same problem as me had SATA drives, while mine is EIDE.  I think its not detecting the cd-rom because Ubuntu has no EIDE support right off the bat, perhaps.

If anyone has had the same problem, or has any ideas on how to get by it, I would be extremely grateful.


Thanks a lot...

---

### Post by Aek on 2005-07-04
I am seeing a similar problem on my new TwinHead Durabook R15D.
Any assistance is appreciated.
I initially had an issue with acpi which i turned off during installation and now i cannot detect the cdrom drive (although i booted off it)

I have tried ide=nodma 

thanks

---

### Post by leonbrooks on 2005-12-15
[QUOTE=Aek]I am seeing a similar problem on my new TwinHead Durabook R15D. now i cannot detect the cdrom drive (although i booted off it)

I have tried ide=nodma [/QUOTE]
That would be because the installer doesn't load SATA drivers that early.

I tried out an R15D today using Mandriva 2006.0 and ran into the same problem. The laptop has **NO TRADITIONAL IDE CONTROLLER AT ALL**, all of the drives on it are SATA including the DVD burner, so if I buy one I'm going to have to do the install over a LAN.

---

### Post by Aek on 2005-12-18
I see. that explains my problem.
Thanks

---

### Post by leonbrooks on 2005-12-28
Oddly enough, the Mandriva installer works if you start it with "linux noauto", but the resulting system locks up on boot (same as Ubuntu) and I haven't yet found out how to simulate the beneficial effects of the "noauto" option.

acpi=off or acpi=ht or noapic will get past the lockup, but none of those options results in a working SATA driver. The ahci module refuses to load by itself, and the aha_piix module sees controllers but no drives.

If anyone's watching this with a view to fixing it, [http://durabook-r15d.cyberknights.com.au/](http://durabook-r15d.cyberknights.com.au/) contains some PCI dumps, dmesg etc. The chipset is an Intel 915.

---

### Post by svitj on 2006-01-20
I have the same problem and I can't solve that.... 
:((
:???:

---

