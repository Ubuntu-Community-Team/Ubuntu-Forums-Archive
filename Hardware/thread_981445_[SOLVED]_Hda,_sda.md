---
title: "[SOLVED] Hda, sda"
date: 2008-11-13
forum: Hardware
---

### Post by theozzlives on 2008-11-13
Everything I read about Linux says an IDE drive is hda. I've got 3 computers (all IDE) and they are assigned as SCSI drives (sda). What gives?

---

### Post by hardyn on 2008-11-13
they found that the sata drivers do a better job than the old ide drivers, so all the devices are now controlled using the sata driver; for ubuntu anyway.

all the things that you read should still work, just keep this change in mind.

---

### Post by RumorsOfWar on 2008-11-18
8.04 is the first linux I've had that had a hard time burning CDs/DVDs. It also has a hard time moving large files. 

Could that be because its using that sata driver?
What log file would tell me?
Can I use synaptic to change back to IDE, or would that screw the install?

---

### Post by theozzlives on 2008-11-19
> **RumorsOfWar said:**
> 8.04 is the first linux I've had that had a hard time burning CDs/DVDs. It also has a hard time moving large files. 

Could that be because its using that sata driver?
What log file would tell me?
Can I use synaptic to change back to IDE, or would that screw the install?

I'm not having any pros burning cd/dvds on my laptop, but am  with my desktop. that drive is 5 yrs old though and I'm just marking it up to a dead drive not the sata drivers.

---

### Post by RumorsOfWar on 2008-11-19
> I'm not having any pros burning cd/dvds on my laptop, but am with my desktop. that drive is 5 yrs old though and I'm just marking it up to a dead drive not the sata drivers.
That's possible, but there are actually a lot of people who are having this problem as of 8.04, and my HD isn't very old. It may be coincidence, but if its the sata driver what log file would show that?

---

