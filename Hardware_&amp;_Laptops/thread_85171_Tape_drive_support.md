---
title: "Tape drive support"
date: 2005-11-01
forum: Hardware &amp; Laptops
---

### Post by Fyrfyter on 2005-11-01
Does Ubuntu support use of a Colorado 250 Jumbo Tape drive?
Thanks

---

### Post by magicfab on 2005-11-01
Search for "ftape" in Synaptic. It appears to be supported, you would need the ftape-utils package. This is the description of ftape-utils:

Bleeding Edge floppy tape driver (utilities)
A substitution for the stock ftape driver in the kernel. If you
want to use a floppy tape drive with a 2.0.x kernel you should definitely
use these sources instead of the stock ftape driver in the kernel.
This driver detects and supports many more tape drives than the
2.0.x driver which is ancient.
Compared to the 2.2.x stock ftape driver the difference is
reduced to support for the Iomega Ditto Max, parallel port floppy
tapes (Colorado Trakker, Iomega, Exabyte and Seagate parallel port
drives) and multiple tape drives in one box.

Supported drives according to upstream README:
"Currently, the driver supports many QIC-40/QIC-80/QIC-3010/QIC-3020
tape drives that conform to the respective QIC-* development
standards, as well as the Iomega Ditto 2GB and Max drives.

Some parallel port tape drives are also supported, too. These are the
Colorado Trakker and several kinds of parallel port drives that use
the Micro Solutions' "Backpack" protocol, i.e. the Iomega Ditto
parallel port drives, and some parallel port floppy tape drives made
by Exabyte and Seagate."

If you want to use the graphical frontend you've got to install a version
of the TK toolkit.

---

