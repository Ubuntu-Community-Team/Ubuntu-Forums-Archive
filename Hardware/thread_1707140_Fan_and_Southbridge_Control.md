---
title: "Fan and Southbridge Control"
date: 2011-03-14
forum: Hardware
---

### Post by xcarguy on 2011-03-14
I've got an Everex Stepnote NC1510, yes I know it's junk but it was free.  I'm loving Ubuntu 10.10 so far with the execption of the system fan.  The machine is all Via chipsets.  Particularly the VT8237A southbridge and C7-M 1.5GHz processor.  I checked with Via and followed their documentation for recompling the kernel with support for the southbridge however the driver script doesn't include definitions for the UDMA 133 protocol.  Does anyone have a clue as how to turn the fan off or at least define the trip points so that they work correctly after loading the Via cpu driver with lm sensors.  I doubled checked the temp reading for the cpu after loading the driver and it was some crazy number like +23548 C.

---

