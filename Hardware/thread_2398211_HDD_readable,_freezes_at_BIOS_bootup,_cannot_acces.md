---
title: "HDD readable, freezes at BIOS bootup, cannot access BIOS"
date: 2018-08-09
forum: Hardware
---

### Post by bulgin on 2018-08-09
I have Ubuntu 16.04 and turned on the 'puter today and the PC freezes at the American Megatrends Logo.
The usual interrupts to access the BIOS don't work, and I hear the hard drive running as though it is working, but it is frozen on the BIOS screen.

I removed the hard drive and inserted an Ubuntu version on a USB which starts up fine and the computer runs as well as accessing the BIOS.

I take the (seemingly) faulty hard drive and connect it to a USB adapter and plug it into another computer and I can read it fine.

While there I ran the grub-recover program and re-inserted the hard drive into the original computer - same thing hangs on BIOS.

So we see the following:

1) Hard drive does not boot up and won't allow operator to access bios controls which should be easily accessible before hard drive starts clicking.
2) Hard drive is easily accessible from another computer.
3) A USB boots fine on the faulty computer and BIOS menus is accessible.
4) After running Grub-recover on the faulty hard drive and re-inserting into computer, same issue happens with computer freezing when a hard drive is present.

Any suggestions?

---

### Post by TheFu on 2018-08-09
Disk controller, SATA cable issues.  Try different cables and SATA ports as a starting point.
But it could be the onboard disk controller too.  USB and SATA commands are NOT the same.

---

