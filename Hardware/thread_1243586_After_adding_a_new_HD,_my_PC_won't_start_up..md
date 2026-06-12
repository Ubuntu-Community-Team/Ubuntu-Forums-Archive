---
title: "After adding a new HD, my PC won't start up."
date: 2009-08-18
forum: Hardware
---

### Post by anthony62490 on 2009-08-18
Not an Ubuntu-specific question, but you people are just so darn helpful...

Anyway. I decided to reinstall Ubuntu on a new HD after some pretty major hardware issues. Every went fine until I tried to attach my old HD as my Primary Slave. 

The computer will start up just fine with only my new HD, but when I attach the old HD, it will only start up the first time. Any time after that and it will shut down within 5 seconds after pushing the power button. If I want to start it up again, I have to unhook the old HD and plug it back in again.

The guts have been set up like so:
> IDE0:
Master = New HD
Slave = Old HD

> IDE1:
Master = DVD Drive
Slvae = N/A


My CMOS is set to detect both Primary drives automatically on startup, so I don't think it's a problem with the CMOS.

Any ideas out there?

---

### Post by markbuntu on 2009-08-18
Did you change the jumper on the old drive so it knows it is now a slave?
You need to do that with IDE drives.

---

### Post by anthony62490 on 2009-08-18
Yes, I did change the jumpers. They are in the correct positions.

---

