---
title: "Zero a hard drive"
date: 2010-01-19
forum: Hardware
---

### Post by PartsMan on 2010-01-19
I know that this has been covered many times but I can't find it in search.

What is the command to zero a hard drive?

Also about how long will it take for 30g?

---

### Post by garryknight on 2010-01-19
For an entire drive: dd if=/dev/zero of=/dev/sda
For a partition: dd if=/dev/zero of=/dev/sda1

Change the sda and sda1 to suit. And be sure to get the if (input file) and of (output file) the right way round or it won't work.

> **PartsMan said:**
> 
Also about how long will it take for 30g?

No idea, but you didn't even say whether it was an SATA drive, a PATA drive, a SCSI drive, or what, so I doubt that anyone else can tell you either.

---

### Post by PartsMan on 2010-01-19
Thanks! It is the original drive in my Dell 2350.
I was just looking for a guess.
 minutes, hours, or days.

---

### Post by pi/roman on 2010-01-19
I'll guess 3 hrs and look forward to hear how far off I was

---

