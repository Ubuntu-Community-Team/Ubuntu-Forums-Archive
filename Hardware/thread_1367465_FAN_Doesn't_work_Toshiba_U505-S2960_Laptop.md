---
title: "FAN Doesn't work Toshiba U505-S2960 Laptop"
date: 2009-12-29
forum: Hardware
---

### Post by madzhu on 2009-12-29
Hi guys,
I'm pretty new with Linux, but since now I LOVE IT.
There is just one problem, the fan won't start spinning.
I have windows 7 ultimate x64 and Ubuntu 9.10 x64.
It is working in Windows 7 but when I start Ubuntu it doesn't want to work.
I updated the BIOS but is the same problem. 
Thanks.

---

### Post by InternetDominus on 2010-03-08
Hi,

I have the same problem with my toshiba U500, were you able to find a solution?

Thanks!

---

### Post by cph05a on 2010-03-08
have you tried this:
[http://swinky-linuxblog.blogspot.com/2009/05/ubuntu-904-on-toshiba-satellite-l305.html](http://swinky-linuxblog.blogspot.com/2009/05/ubuntu-904-on-toshiba-satellite-l305.html)

---

### Post by khelben1979 on 2010-03-08
If you're able to use Ubuntu without the fan spinning, you can start with looking into different software which uses the [lmsensors]("http://en.wikipedia.org/wiki/Lm_sensors") package.

```
sudo apt-get install ksensors
``` is one of them, but here's a list which include more of them.

If the Linux kernel isn't able to identify your hardware in your laptop very good, no software package will help you in this situation, so let's hope for the best.

---

### Post by k33bz on 2010-03-30
you might want to try this

[http://michaelminn.com/linux/toshiba-u505/]("http://michaelminn.com/linux/toshiba-u505/")

---

### Post by finito on 2010-04-29
[http://art.ubuntuforums.org/showthread.php?t=1420247&highlight=toshiba+U505+fan&page=2](http://art.ubuntuforums.org/showthread.php?t=1420247&highlight=toshiba+U505+fan&page=2)

I got the fan to work

---

