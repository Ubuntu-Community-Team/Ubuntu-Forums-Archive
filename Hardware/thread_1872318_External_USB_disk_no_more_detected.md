---
title: "External USB disk no more detected"
date: 2011-10-30
forum: Hardware
---

### Post by Shocker on 2011-10-30
Hello everybody!

It's a couple of days that a Trekstor USB HDD (160 GB Datastation Maxi n.u model) is not detected anymore.

The disk seems to correctly spin-up when turned on and does not give bad sounds but only those typical of the searching and working phases.

but

lsusb output is:

shocker@OO64:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 003: ID 046d:c626 Logitech, Inc. 3Dconnexion Space Navigator 3D Mouse
Bus 002 Device 004: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser

and fdisk -l does not detedt the usb drive.

Any hint to get it back to work?

Thanks in advance!

Shocker!

---

