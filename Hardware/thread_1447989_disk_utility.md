---
title: "disk utility"
date: 2010-04-06
forum: Hardware
---

### Post by sn0m on 2010-04-06
Hi Chaps
Does any of you know how to turn SMART on in disk utility.
I have enabled it in bios but disk utility reports it as unavailable.
Reg
Sokol

---

### Post by gradinaruvasile on 2010-04-06
What version of Ubuntu do you use?

And what type of HDD do you have?
First, the HDD must support SMART - i think  all SATA drives have it. But older IDE ones might not support it..
Second, you have to enable it in BIOS - as you have done.
Third, if you have AHCI mode in BIOS, enable it. Do not leave SATA HDD on IDE emulation mode, it might be slower, AHCI mode is fully supported in Linux (Windows XP doesnt support it OOTB).
If you are absolutely sure that your HDD supports SMART, BIOS supports it and its enabled but it doesnt show up in Ubuntu's disk utility, try installing smartmontools.

---

### Post by sn0m on 2010-04-06
hi there
thanks for your reply
AHCI mode is on.
SMART in bios is on.
still no joy with disk utility.
I am using smart tools at present
:koli@koli-laptop:~$ sudo smartctl -H /dev/sda
[sudo] password for koli: 
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

koli@koli-laptop:~$ 

but I find disk utility quite handy and it will give notice if disk is failing.
So no joy for time being.
regards
Sokol

---

### Post by gradinaruvasile on 2010-04-06
sudo smartctl --all /dev/sda 

will give you more results...

Anyway, what version of Ubuntu do you have?

---

