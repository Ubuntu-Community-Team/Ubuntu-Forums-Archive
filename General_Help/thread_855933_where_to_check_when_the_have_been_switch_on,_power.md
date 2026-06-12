---
title: "where to check when the have been switch on, poweroff and restart?"
date: 2008-07-11
forum: General Help
---

### Post by afeasfaerw23231233 on 2008-07-11
my box recently restarted and shut down abnormally (in the late night when i am not using it. the system log doesn't tell the time it was powered on, shut down or restart. is there anyway to get the information?

---

### Post by VMC on 2008-07-11
There are messges in "/var/log" . Look at "/var/log/messages" and look for your error.
Also 'dmesg' some some error messages maybe of value. Type that from a Terminal.

---

