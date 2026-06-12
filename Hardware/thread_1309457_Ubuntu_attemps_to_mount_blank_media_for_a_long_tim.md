---
title: "Ubuntu attemps to mount blank media for a long time"
date: 2009-11-01
forum: Hardware
---

### Post by dE_logics on 2009-11-01
I insert a blank media...and does something with it for a long time (read operations on disk)...I think it attempts to mount it.


Point is this should not happen, once the disk is inserted it should just recognize it as blank rather than taking 3 - 4 minutes in an attempt to mount it.

---

### Post by dE_logics on 2009-11-01
The hald process was causing the problem...need to consult it's man page for further configuration.

For the mean time, the remedy is to stop the process.

---

