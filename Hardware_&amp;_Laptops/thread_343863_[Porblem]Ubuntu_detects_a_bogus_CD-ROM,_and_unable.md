---
title: "[Porblem]Ubuntu detects a bogus CD-ROM, and unable to boot system."
date: 2007-01-22
forum: Hardware &amp; Laptops
---

### Post by keyi22 on 2007-01-22
I have two hard drivers on IDE1: [COLOR="RoyalBlue"]hda[/COLOR] & [COLOR="RoyalBlue"]hdb[/COLOR], and one CD driver on IDE2: [COLOR="RoyalBlue"]hdc[/COLOR].
After I substituted a new CD-ROM for the old one, there appears another [COLOR="DarkOrange"]hdd[/COLOR] under /dev/.
In fact, I have only one CD driver!
Every time I boot the system, the kernel ring tells:

[4294671.758000]     ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:DMA, hdd:pio
[4294673.561000] hdd: SCR-830, ATAPI CD/DVD-ROM drive
[4294675.841000] hdd: status error: status=0x00 { }
[4294675.841000] hdd: status error: status=0x00 { }
[4294675.841000] hdd: status error: status=0x00 { }
[4294675.841000] hdd: status error: status=0x00 { }
[4294675.891000] hdd: ATAPI reset complete
[4294675.891000] hdd: status error: status=0x00 { }
[4294675.891000] hdd: status error: status=0x00 { }
[4294675.891000] hdd: status error: status=0x00 { }
[4294675.891000] hdd: status error: status=0x00 { }
[4294675.941000] hdd: ATAPI reset complete
[4294675.941000] hdd: status error: status=0x00 { }
[4294675.941000] hdd: ATAPI CD-ROM drive, 0kB Cache
... 

How can I get rid of this bogus device [COLOR="DarkOrange"]hdd[/COLOR]?
Thanks a lot!

---

### Post by skewray on 2007-01-23
Sounds like a hardware problem.  Most likely the jumper is wrong on the cd-rom.  If the cd-rom is alone on a cable, make sure that it is at the end and jumpered as master or select.  Some drives have a "single" setting as well.  If it shares a cable with a hard drive, try to position it in the middle of the cable and as a slave or select.  I am a little fuzzy on this, so a google search on "ide slave master" should give you lots of good information by those in the know.

---

