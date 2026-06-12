---
title: "Wont mount drive or boot with system clock reset"
date: 2010-01-25
forum: Hardware
---

### Post by shedonlie on 2010-01-25
I'm a noob so i'm not sure whether this should be addressed as an issue or just be left as is.  My laptop ran dry and my battery to keep the clock is dead too.  The system clock was reset to 2008 and Ubuntu wouldn't mount the drive hence wouldnt boot.  I have no idea how to set something like that from the command line so good thing i have a windows partition.  when i used windows to sync the clock, ubuntu was back to normal.

is setting the system clock from the command line common knowledge or should there be some kind of check for this?

didnt think about it till now - i might have been able to use my bios to set the clock too..

if someone could help me with how to set that clock that'd be great.

thanks

---

### Post by efflandt on 2010-01-25
Yes, for every computer I have used you can set the BIOS (hardware) clock from CMOS setup during boot (even without any OS).

For setting those in terminal see **man date** (system clock) and **man hwclock** (BIOS clock calendar).  Note that you may need to use sudo.  Or **apropos date** and **apropos time** would give you more man pages to read.  "apropos" is a command to search for manpage keywords if you do not really know what command you are looking for.

---

