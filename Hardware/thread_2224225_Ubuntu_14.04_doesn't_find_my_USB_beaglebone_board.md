---
title: "Ubuntu 14.04 doesn't find my USB beaglebone board"
date: 2014-05-15
forum: Hardware
---

### Post by xxlray on 2014-05-15
I have an experimental Beaglebone Board (somehow similar to a Rasberry Pi). In Ubuntu 12.04 I could just connect it to my computer's USB port and Ubuntu recognized it as storage device. Now I upgraded to Ubuntu 14.04 on my computer (no clean re-install) and the computer does not react when I attach the board.

I have no idea which log to check for errors as /var/log/syslog only contains kernel messages of the following type:```
62042.672157] evbug: Event. Dev: input22, Type: 0, Code: 0, Value: 0
```

Other devices like my USB stick, mouse or keyboard are recognized like before the update.

---

