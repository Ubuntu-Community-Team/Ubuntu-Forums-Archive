---
title: "HP 5300C scanner is not working"
date: 2006-08-08
forum: Hardware &amp; Laptops
---

### Post by dyrer on 2006-08-08
Hello,
I have a scanner 5300C and used to work with any linux distro except 6.06
Now with xsane preview is working but scan procedure freezes and receive error message and scanner freeze and light is flashing
Anyone can help setup correct my scanner?

---

### Post by zxee on 2006-08-08
Have you gone to the SANE site and looked for an update to the backend for your scanner? [http://www.sane-project.org/cgi-bin/driver.pl?manu=hewlett+packard&model=5300c&bus=any&v=&p=](http://www.sane-project.org/cgi-bin/driver.pl?manu=hewlett+packard&model=5300c&bus=any&v=&p=)
I wonder if it works in breezy?
You may need to file a bug report with the ubuntu developers.
[https://launchpad.net/distros/ubuntu/+bugs](https://launchpad.net/distros/ubuntu/+bugs)

---

### Post by dyrer on 2006-08-10
SANE has a backend but how can setup and configure

(Newbie here)

---

### Post by Psykotik on 2006-08-13
It seems like we are many to have [this problem]("http://forum.ubuntu-fr.org/viewtopic.php?id=53149")...

---

### Post by LARFWOOD on 2006-08-16
I had the same problem.
For me it was fixed after changing the dpi to 300
Now it is working fine
Good Luck

---

### Post by Psykotik on 2006-08-19
I was quite skeptical, but changing the dpi option to 300 did the trick !

Well, it is not exactly the best solution one can expect, but it works well.

Thanks Larfwood.

---

