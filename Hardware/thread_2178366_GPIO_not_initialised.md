---
title: "GPIO not initialised"
date: 2013-10-03
forum: Hardware
---

### Post by e-San on 2013-10-03
Hi!

I'm trying to run flashrom on my P4 platform.
I installed ubuntu server 12.04 and compiled flashrom.

Reading works fine, but not writing. We found that there is a problem with initialision of GPIO interface:

```
[    7.648624] lpc_ich 0000:00:1f.0: I/O space for GPIO uninitialized
```

and

```
root@flashrom:/home/san# echo 13 > /sys/class/gpio/export
bash: echo: write error: Invalid argument
```

What can i do to enable GPIO?

Log, dmesg and other possibly useful files are located here:
[http://e-san.info/Abit_IS7/](http://e-san.info/Abit_IS7/)

Regards!

---

