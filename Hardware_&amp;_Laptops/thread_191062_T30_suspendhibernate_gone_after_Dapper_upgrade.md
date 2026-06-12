---
title: "T30: suspend/hibernate gone after Dapper upgrade"
date: 2006-06-07
forum: Hardware &amp; Laptops
---

### Post by woodsworth on 2006-06-07
Just what the subject line says—I upgraded to dapper, by changing sources and using the command line, and not only do my hotkeys not work, but typing "hibernate" in Konsole gives me this:

> root@ubuntu:~# hibernate
Your kernel does not appear to have Software Suspend 2 support compiled in.
Please follow the HOWTO linked from [http://www.suspend2.net/](http://www.suspend2.net/) for instructions
on how to compile Software Suspend into your kernel.
hibernate: Aborting.

Where do I start?

---

### Post by caldevil on 2006-06-07
Hibernate is for software suspend 2. Ubuntu uses software suspend. Try

> 
/etc/acpi/hibernate.sh


---

### Post by woodsworth on 2006-06-07
Either way, Fn + F4 doesn't suspend to disk, and Fn + F12 doesn't suspend to ram.

---

