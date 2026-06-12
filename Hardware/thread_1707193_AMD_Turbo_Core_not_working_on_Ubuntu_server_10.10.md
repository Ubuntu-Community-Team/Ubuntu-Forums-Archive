---
title: "AMD Turbo Core not working on Ubuntu server 10.10"
date: 2011-03-15
forum: Hardware
---

### Post by baosheng on 2011-03-15
I have installed Ubuntu server 10.10 on my new computer which uses AMD Phenom II X6 1090T. 

But I have noticed that my CPU cores were not able to run at 3.6GHz at any time, even when I only have one CPU-intensive computing job. They are either at 3.2 GHz or 800 MHz, like this

```
$ cat /proc/cpuinfo | grep -i "cpu Mhz"
cpu MHz		: 800.000
cpu MHz		: 3200.000
cpu MHz		: 3200.000
cpu MHz		: 800.000
cpu MHz		: 800.000
cpu MHz		: 800.000

```

My maximum CPU frequency seems to be locked at 3.2 Ghz:
```
$ dmesg | grep "pstate 0"
[    1.595918] powernow-k8:    0 : pstate 0 (3200 MHz)

```

I googled around and it seems that Linux 2.8.35 kernel have solved the problem. I just do not understand why it does not work on mine. 

```
$ uname -a
Linux hogwarts 2.6.35-22-server #35-Ubuntu SMP Sat Oct 16 22:02:33 UTC 2010 x86_64 GNU/Linux

```

Does anyone have any idea?

---

