---
title: "Hardy Xorg bug?"
date: 2009-01-14
forum: Hardware
---

### Post by frogotronic on 2009-01-14
Hello,

  I think xorg has a bug in it.  It doesn't read the correct DisplaySize using the fglrx driver.  Specifiying DisplaySize in the xorg.conf files fixes this, but when connecting my laptop to external monitor and aspect ratios are wrong on XINE, TOTEM, MIRO (all Xine backends).

  Xorg and FGLRX should be able to read the EDID from the monitor.  Unfortunately, unlike nVIDIA's driver this feature appears to be lacking.

Does/has anyone else encountered this xorg/aspect bug?

- CH  :confused:

---

