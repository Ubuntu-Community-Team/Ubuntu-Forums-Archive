---
title: "Canon Pixma iP1000: &quot;No %%BoundingBox: comment in header!&quot;"
date: 2007-02-10
forum: Hardware &amp; Laptops
---

### Post by CPUFreak91 on 2007-02-10
Hi, I've followed numerous instructions to get a Canon Pixma iP1000 printer working under Ubuntu (I'm using edgy) but it doesn't work. The GUI doesn't provide me with much information, but the cups web interface ([http://localhost:631/printers/](http://localhost:631/printers/)) tells me: "No %%BoundingBox: comment in header!"

What could be causing this?
Thanks.

---

### Post by gosh on 2007-03-10
I have the same problem with my HP C3180 through a Belkin print server.
Under Edgy it worked perfectly with lpd://192.168.2.253/lp1.
Now I get in the /var/log/cups/error_log 

No %%BoundingBox: comment in header!

---

### Post by Dumdideldum on 2007-03-17
Same problem and error message with IP4200 (Canon Drivers) under Feisty Fawn, latest updates.

---

### Post by Dumdideldum on 2007-03-17
Solved it now.
First of all, in the /etc/cups/cupsd.conf - 
LogLevel Debug instead of Loglevel warning.

Now you can examine the /var/log/error_log deeper.

I did two things, one found via google:

edit the /etc/udev/rules.d/45-libgphoto2.rules
and rename all ATTRS entries into SYSFS entries.

Secondly, and I think this was just my problem, I found via debug level, that cups couldn´t find libpng.so.3 - don´t ask me why.

a quick apt-get --reinstall install libpng3 solved my problems - the printer works like a charm again.

---

### Post by CPUFreak91 on 2007-03-17
Thank you very much. This works perfectly. Now my Dad doesn't have an excuse to boot into windows ;).

---

### Post by ubu-for on 2007-05-12
> **Dumdideldum said:**
> Solved it now.
First of all, in the /etc/cups/cupsd.conf - 
LogLevel Debug instead of Loglevel warning.

Now you can examine the /var/log/error_log deeper.

I did two things, one found via google:

edit the /etc/udev/rules.d/45-libgphoto2.rules
and rename all ATTRS entries into SYSFS entries.

Secondly, and I think this was just my problem, I found via debug level, that cups couldn´t find libpng.so.3 - don´t ask me why.

a quick apt-get --reinstall install libpng3 solved my problems - the printer works like a charm again.

Both workarounds didn't work for my "Brother MFC" with USB.

Any further ideas?

THX!

---

