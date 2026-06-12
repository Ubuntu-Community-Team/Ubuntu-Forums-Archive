---
title: "TRENDnet NIC"
date: 2007-03-27
forum: Hardware &amp; Laptops
---

### Post by peterhf on 2007-03-27
Ubuntu desktop 6.10 has been installed on a Dell OptiPlex GX100. Neither the motherboard-based NIC nor a D-Link NIC would work after being correctly configured. Assumed that the a Linux driver is not present for either NIC. A TRENDnet NIC, TEC-PCITXR, was purchased because the box indicated that the NIC is appropriate for Linux and installed. "Out of the box" this NIC didn't work either. The CD contains directories for Linux 2.2.x and 2.4.x each containing a Makefile and a C source file.

Contact with the Support people resulted in "You have the latest version.".

When I run "make", this message appears"

make: *** no rule to make target `/usr/include/linux/version.h'. needed by `r8169.o'. Stop.

Help will be appreciated!

Peter -

---

### Post by scrooge_74 on 2007-03-27
you first need to run the config command before doing a make command followed by a sudo make install

when you do the config part the system may tell you which libraries you dont have, you will have to install those first before continuing on.  Check the instructions for how to compile the drivers for your card.

Good luck

---

