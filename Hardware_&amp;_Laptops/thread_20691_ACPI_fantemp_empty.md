---
title: "ACPI fan/temp empty"
date: 2005-03-18
forum: Hardware &amp; Laptops
---

### Post by jpt2433 on 2005-03-18
I just installed Ubuntu on my laptop (a semi-custom job, bears resemblance to a CL56) and I like it.  I'm very concerned that the laptop may be getting too hot, I haven't had any problems, but it feels warm and when I tried checking temperature with acpi I found that it wasn't supported.  I also found that the /proc/acpi/fan and thermal directories are empty.  

I messed around with a variety of options that I found (lm-sensors and several monitors which ended up relying on the acpi stuff) but nothing ended up working so far. 

Does anyone have any advice?  It seems like the opposite problem (fans running too much) is more common.  What does it mean if those directories are empty?

Any help will be greatly appreciated, I'd like to move this laptop to Ubuntu only so I can do linux development.

---

### Post by briguy on 2005-03-18
Check out [http://acpi.sourceforge.net/](http://acpi.sourceforge.net/) for more info on linux and acpi.  There are also a few good posts in the forum here - search for dsdt.

Good luck.

---

