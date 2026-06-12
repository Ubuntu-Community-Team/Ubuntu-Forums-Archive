---
title: "Installation hang up!"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by noxp on 2009-10-29
Hi Guys! I downloaded ubuntu 9.04 and 8.04 and used infrarecorder_8741 to burn the disks but when I try to install them they both hang up when it gets to "Copying files". Could it be the downloads or the burner? :(

---

### Post by lemming465 on 2009-10-30
> Could it be the downloads or the burner?

Could be any of: bad download, bad CD burn, bad memory, bad hard drive, buggy disk controller chipset that isn't supported well by Linux, ... lots of room for problems.

First try the "Test Memory" (runs memtest86+) boot option for about 20 minutes and see if you have any obvious memory problems.  

Assuming not, then use the "Check disk for defects" boot option to validate the disk as burned.  

If it doesn't pass, try burning at a slower rate.  If the second burn doesn't pass, download one of the checksum files and verify the .ISO image file is correct.  (Us paranoid types use the SHA256SUM files and a tool like sha256deep, plus we validate the GPG signature.)

If the memory and disk both pass, but you still can't install, try a 9.10 CD to see if that's any better. 

If not, write back with more details on the symptoms.

---

