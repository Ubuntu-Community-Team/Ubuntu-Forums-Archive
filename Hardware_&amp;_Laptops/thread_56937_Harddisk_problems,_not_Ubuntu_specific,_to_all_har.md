---
title: "Harddisk problems, not Ubuntu specific, to all hardware specialists :)"
date: 2005-08-14
forum: Hardware &amp; Laptops
---

### Post by phen on 2005-08-14
hello!

im using a 4 month old hp laptop nc6120. it has got a 60gb hdd with the hp data protection technology (whatever that means...). 

i have got strange problems with this harddisk. about once in two weeks, the / partition hda4 is set to read-only access by the OS, because of some strange hardware errros. when rebooting, i have to run fsck.ext3 manually. 

there i am asked to fix inodes (hundreds of them!!!). i can recall the error messages to be:

EXT3-fs error (device hda4) in start_transaction: read_only

usually, running fsck fixes the hdd for 2 weeks, this time it didn't help much. A harddisk diagnosis tool from the bios brings no errors. what could i do?
what could the problem be?
is it possible, that repartitioning the harddisk would help?


thanks for help,

Kai

---

### Post by nad on 2005-08-14
From the HP site:

"HP Drivelock helps prevent the data on your hard drive from being compromised even if your notebook is lost or stolen."

This utility is probably hardcoded into a chip in your computer or a hidden partition and is being run automatically.

Please request help from HP as they advertise this machine without an operating system.

---

