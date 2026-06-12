---
title: "External Hard Drive"
date: 2008-09-07
forum: Hardware
---

### Post by Nalroff on 2008-09-07
Ok, so I have a WD 320 Portable HDD with Ubuntu installed. It works wonderfully after setting the boot config file <menu.lst> to boot to (hd0,0) because for some reason, my comp recognizes the PHDD as hd0 rather than the internal hard drive. Oh well, everything is good on that end.

The problem, however, is that when I put my computer into suspend mode (haven't tried to do hibernate yet) and bring it back up, i get a long list of command line error messages, all saying something about finding hd1. I was wondering if there was a way to remedy this. I would give the error report it gives me, but it moves constantly and Ubuntu never actually does come back to the Desktop.

Thanks,
Nalroff

<edit>

It seems that the error message is a repeat of the same message over and over, and then a block of similar messages before the whole process repeats. This is what it gives me:

EXT3-fs error (device sdb1): ext3_find_entry: reading directory #10**** offset 0
<where the **** are variable numbers that change>

and then

Buffer I/O error on device sdb1, logical block 1

hope this helps.

---

