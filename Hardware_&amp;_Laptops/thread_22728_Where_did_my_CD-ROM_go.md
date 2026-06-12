---
title: "Where did my CD-ROM go?"
date: 2005-03-29
forum: Hardware &amp; Laptops
---

### Post by askreet on 2005-03-29
Original Install Configuration:
sda - 80 GB SATA (Linux)
sdb - 36 GB SATA (Windows)
scd0 - NEC DVD+-RW
scd1 - CDROM drive.
stock 386 kernel.

I just booted back to linux for the first time in a few weeks after removing my cdrom and giving it to a friend of mine.. I then installed 686-smp kernel, and nvidia modules restricted-modules etc etc for it. Rebooted, Direct Rendering: Yes.

All is well, right?

Wrong.

I have no /dev/hd* no /dev/scd* -- nothing but my hard disks.

I wonder outloud if it's the new kernel so I boot back to 386 and no X works (since nvidia modules isnt loaded for it.) so I'm in root console and I cant find /dev/hd* or /dev/scd* -- but theres a /dev/sr0 which is IN FACT my dvd+rw drive.. Cool beans I say, it must have been renamed in a patch.. no biggie.

I boot back to 686-smp and theres no sr0, just sda* and sdb* --

Anyone have ANY idea? lspci DOES show the ATA/100 controller... but /dev is bare of any CDROM names that i'm familiar with.

Please any help is greatly appreciated. I was on IRC all last night, to no avail.

Thanks in advance,
 Skreet

---

