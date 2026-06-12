---
title: "Error Disk has too many bad sectors"
date: 2010-03-09
forum: Hardware
---

### Post by al's on 2010-03-09
The first time I opened Ubuntu, that error report popped up. What should I do. 
An image of the error is attached.

---

### Post by tgalati4 on 2010-03-09
It's possible that it's a misinterpretation of SMART data.  First, take a flash drive and backup any critical data on that drive.

Post the output of:

sudo badblocks /dev/sda1

How many power-on hours does this drive have on it?

---

### Post by Rick Deckard on 2010-03-09
I posted about this yesterday - it's a known bug.

See my post [here]("http://ubuntuforums.org/showthread.php?p=8934413#post8934413").

---

### Post by tgalati4 on 2010-03-09
Or a bug . . .

---

