---
title: "Time Zone Problem"
date: 2008-08-12
forum: General Help
---

### Post by skirby on 2008-08-12
I have an Ubuntu 8.04 Server connected to a Windows 2003 Active Directory domain.  I want to set the time zone to GMT, as is the AD, but there appears no choice in the time zone settings.  So I used Europe/London; Greenwich is near London isn't it?  When I use that setting, the time is one hour off, so I had to use Azores, which is the correct time.  Can anyone help me here.  I am pretty new at Linux.

Thanks, 
  Steven

---

### Post by pauper on 2008-08-12
UK is on Summer Time (UTC+1) till 26 October. Try later :)?


[http://wwp.greenwichmeantime.com/time-zone/europe/uk/](http://wwp.greenwichmeantime.com/time-zone/europe/uk/)

---

### Post by skirby on 2008-08-19
OK, so how I do I set my Ubuntu 8.04 server to GMT?

---

### Post by pauper on 2008-08-19
You might find an answer [here](http://www.debian.org/doc/manuals/system-administrator/ch-sysadmin-time.html). Please, read the entire chapter.

Try changing "UTC=yes" to "UTC=no" in /etc/default/rcS.

Other than that, I guess, you would use Azores timezone from 1 a.m. UTC on the
last Sunday in March and to 1 a.m. UTC on the last Sunday in October, and UK
one for the other part of the year.

---

