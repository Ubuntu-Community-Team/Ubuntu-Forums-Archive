---
title: "Wintech ultimate bicycle computer"
date: 2010-04-30
forum: Hardware
---

### Post by geoffrussell on 2010-04-30
Does anybody know how to mount and read data from a USB
Wintech Ultimate bicycle computer. When I plug it in,
I see "cp2101 converter now attached to ttyUSB0" appear on
/var/log/messages, so it is recognised.

But I don't quite know how to access the device.

Any ideas?

---

### Post by Fafler on 2010-04-30
You need some software to read and parse the data. The good thing is that it's recognized as a standard serial port. You could try talking to it with minicom, maybe you're in luck and everythings cleartext.

---

