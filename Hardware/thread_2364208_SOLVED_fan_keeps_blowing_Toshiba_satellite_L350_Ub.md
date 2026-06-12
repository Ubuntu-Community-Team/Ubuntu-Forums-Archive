---
title: "SOLVED fan keeps blowing Toshiba satellite L350 Ubuntu 16.04"
date: 2017-06-20
forum: Hardware
---

### Post by adriaan4 on 2017-06-20
After installing lm-sensors and Psensor and playing around, I noticed that my when FAN(s) would start and then never slow down anymore.

After searching many old or irrelevant posts, this worked for me: 
[http://bitjunkieblog.blogspot.nl/2011/08/solution-for-fan-problems-in-ubuntu.html](http://bitjunkieblog.blogspot.nl/2011/08/solution-for-fan-problems-in-ubuntu.html)

Change the file /etc/default/grub
```
vi /etc/default/grub
```

change
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash "
```

to
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=\&#8221;Linux\&#8221;&#8221;
```

And do not forget to run
```
update-grub
```

And then you need to reboot. Beware: the escape chars \&#8221;Linux\&#8221; are important!
Hopes this helps others too.

Version: Linux 4.4.0-79-generic
(you can check that with ```
uname -a
```)

---

### Post by RobGoss on 2017-06-20
Thanks so much for posting your solution I'm sure others will benefit from it

---

### Post by mörgæs on 2017-06-20
Thanks but please use Thread Tools for marking the thread solved. It will help other people searching for an answer.

---

