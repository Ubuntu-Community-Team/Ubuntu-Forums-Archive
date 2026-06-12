---
title: "Problems with serial communication"
date: 2008-06-21
forum: Hardware
---

### Post by sbe on 2008-06-21
Hello,

I just installed Ubuntu Server 8.04 as a replacement for 6.10 which worked quite well for a long time. I use this machine for weather statistics together with a serial receiver for my sensors.

But after upgrading to 8.04 the serial communication for my receiver does not work anymore. I receive a "I/O possible" statement from the program that processes the data form the sensors. Even a "cat /dev/ttyS0" does not work, snooper does not work also:

```
root@home:~# snooper -b19200 /dev/ttyS0
no device specified
```

Does anybody have an idea what has changed between 6.10 and 8.04 regarding serial communication (which is not so common today, I know ;-)?

The problem occurs for others as well, as stated [here]("http://sourceware.org/ml/gdb/2005-10/msg00228.html"), but without a solution.

Regards,
Stefan

---

### Post by imog on 2008-07-01
> **sbe said:**
> Hello,

I just installed Ubuntu Server 8.04 as a replacement for 6.10 which worked quite well for a long time. I use this machine for weather statistics together with a serial receiver for my sensors.

But after upgrading to 8.04 the serial communication for my receiver does not work anymore. I receive a "I/O possible" statement from the program that processes the data form the sensors. Even a "cat /dev/ttyS0" does not work, snooper does not work also:

```
root@home:~# snooper -b19200 /dev/ttyS0
no device specified
```

Does anybody have an idea what has changed between 6.10 and 8.04 regarding serial communication (which is not so common today, I know ;-)?

The problem occurs for others as well, as stated [here]("http://sourceware.org/ml/gdb/2005-10/msg00228.html"), but without a solution.

Regards,
Stefan

Maybe not applicable, but are you sure ttyS0 is the proper device for the serial port you are trying to use?

try "dmesg | grep tty" in a terminal and make sure your specifing the serial port correctly.

---

### Post by sbe on 2008-07-04
> **imog said:**
> Maybe not applicable, but are you sure ttyS0 is the proper device for the serial port you are trying to use?

try "dmesg | grep tty" in a terminal and make sure your specifing the serial port correctly.

Yes of course I'm sure, because it was ok with 6.10 for two years. ;-)

This has already identified as a bug, see [here]("https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/211801").

Regards,
Stefan

---

