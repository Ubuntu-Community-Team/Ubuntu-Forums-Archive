---
title: "tty error: device descriptor read/all -71"
date: 2010-11-28
forum: Hardware
---

### Post by jazzerit on 2010-11-28
(I hope this is the right place for this thread)
On any TTY (1 through 6) I am getting an error:
**USB 1-7: device descriptor read/all , error -71**

Can somebody please:
a) tell me what this error means (google reveals nothing about this)
and
b) tell me either how to fix it or suppress the message (it gets really annoying if I'm trying to do something inside a tty and that message keeps coming up.)

Any help appreciated, but it's not particualarly high priority- more of an annoyance. Thanks.

---

### Post by jazzerit on 2010-11-29
bump

---

### Post by jazzerit on 2010-12-01
second bump...

---

### Post by jazzerit on 2010-12-03
In case anybody else has this issue, I found out how to suppress the message:

First, I had to open /etc/sysctl.conf
then, I had to uncomment the line **#kernel.printk = 3 4 1 3** so that it looked like this: **kernel.printk = 3 4 1 3**
Lastly, I did a restart.

All that does is suppress low-level messages from appearing in a console. To find out how to do it, though, took a lot of digging. This should probably be more easy to find out what the problem is. I still only just know what the problem actually is, because I saw the dmesg output. Anyway, marking as solved.

---

