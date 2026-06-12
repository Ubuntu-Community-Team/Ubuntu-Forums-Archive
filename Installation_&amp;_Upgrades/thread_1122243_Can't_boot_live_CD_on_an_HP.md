---
title: "Can't boot live CD on an HP"
date: 2009-04-10
forum: Installation &amp; Upgrades
---

### Post by f37u5g0d on 2009-04-10
So I try to boot the live CD.  Right off the bat I have to use the noapic option to avoid a kernel panic.  I got the orange bar slides back and forth splash screen and after about 40 seconds I am dropped to a terminal that says:

"Instructions on how to use busy box" <-Loosely quoted

(initramfs)

"ata6.00: status: {DRDY }
ata6.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
ata6.00: cmd a0/00 00 ... ... etc etc blah blah blah ends with
"(timeout)"

Edit: Sometimes the 6 in "ata6.xx" is a 2 or another number.
It then prints this to the screen several times after informing me that:
"ata6: WARNING:  synchronous scsi scan failed without making any progress, switching to async"

It then prints the previous thing (ata6.00 ...) over and over again.  What should I do??  What are some of the kernel options I can pass??

Thank you!!!

---

### Post by f37u5g0d on 2009-04-11
This is on an HP pavilion a1340n if that makes a difference.

I just tried again this morning with the splash and noapic options on the kernel.  (Without quite)
and according to the little boot text I am stuck at

"Running /scripts/casper-premount"

I hope this might help.

BUMP

---

### Post by f37u5g0d on 2009-04-12
I turned off my onboard lan option in my bios and was able to boot.  I am going to start a new thread related to my problems now.

---

