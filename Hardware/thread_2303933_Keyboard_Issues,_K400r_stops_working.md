---
title: "Keyboard Issues, K400r stops working"
date: 2015-11-22
forum: Hardware
---

### Post by Jarubell on 2015-11-22
I'm new to Ubuntu with 12.04 then a few months back upgraded to 14.04. My keyboard worked no problem with the older version, now it only works when I turn the machine on, but when I come back to it later, it has stopped working. 

I have searched the forums, but still lost.

What can I do to get help with my issue?

---

### Post by mörgæs on 2015-11-23
How does it work in a live boot?

---

### Post by Jarubell on 2015-11-26
I'll have to take a look what live boot is but the keyboard works every time after start up or restart.

---

### Post by tgalati4 on 2015-11-27
Look through your log files for any keyboard, input-related, or USB-related errors.

Open a terminal:

```
more /var/log/syslog
```

Spacebar to page forward.  "q" to quit.

---

