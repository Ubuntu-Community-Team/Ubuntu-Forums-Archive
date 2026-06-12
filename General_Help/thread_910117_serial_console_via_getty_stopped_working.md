---
title: "serial console via getty stopped working"
date: 2008-09-04
forum: General Help
---

### Post by Doug_M on 2008-09-04
Hi, yesterday I set up my Apple II (yes, seriously) as a serial console connected to my laptop running Hardy.  I copied one of the tty files in event.d to ttyS0 and modified it like so:

```
/sbin/getty -L 19200 ttyS0 vt220
```

and it worked perfectly with the terminal software running on the Apple (it supports vt220).  I used it all throughout the day without any problems.  

Today I boot the Apple (and terminal software) and I don't get a login prompt.  I killed the getty process for ttyS0 and it respawned as expected.  When it respawned the login prompt showed up on the Apple but it doesn't accept any input, as if it is now a one-way (laptop to Apple) connection.

I've been troubleshooting it for a couple of hours now, trying different options in the terminal program and different getty options and haven't had any success.

Is there some security in place that prevents incoming connections over ttyS0 that may have been off and is now on?

Thanks,
Doug

---

### Post by liggyman on 2009-05-14
Did you ever get this resolved?

I am currently having what appears to be the same issue.

Connect to Hardy via serial console, hit enter get nothing.  On the server I run stop ttyS0 && start ttyS0 and I get a login prompt on the client but can't interact with it.

Any help with this is greatly appreciated.

Thanks!

---

### Post by Doug_M on 2009-05-14
No

---

