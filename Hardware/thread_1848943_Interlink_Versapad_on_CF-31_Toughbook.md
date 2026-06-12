---
title: "Interlink Versapad on CF-31 Toughbook"
date: 2011-09-23
forum: Hardware
---

### Post by summersab on 2011-09-23
It works in the out of the box Windows 7, but not on Ubuntu (or Backtrack, which is my goal). This is a fairly new device from what I can tell. It's listed as PS/2 as far as the interface. Can anyone provide direction on drivers for this?

Thanks!

---

### Post by benmesander on 2012-01-17
Hi,

  You should be able to use the psmouse module as a driver. However, please note you must supply the argument:

proto=base

  Or the pad will lock up, requiring a complete power cycle to restart.

---

