---
title: "New Dell won't boot Hardy live cd"
date: 2008-07-09
forum: Hardware
---

### Post by kryos on 2008-07-09
Boot order is correct.  CD boots on various other machines (older biege box running Dapper, and corporate Dell laptop [D 600] running XP).
Some details of machine are:
Inspiron 530/Core 2 Duo E8300/3 gigs/Integrated Intel Graphics Media Accelerator 3100/Vista Home Premium SP 1.  Displays gibberish (to me) over and over again.  Was thinking about another one of these for Hardy but not if it isn't ready.  Anything sound obvious?
I know that this is probably much more machine than necessary but as I don't replace them often I would like something that will last awhile.

---

### Post by Aearenda on 2008-07-09
There's a thread on the 530 in the forums. It boils down to setting the SATA drives to 'RAID' mode (misnamed), or booting with the all_generic_ide kernel flag.

See [http://ubuntuforums.org/showthread.php?t=762257](http://ubuntuforums.org/showthread.php?t=762257)

---

