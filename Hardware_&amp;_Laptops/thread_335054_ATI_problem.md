---
title: "ATI problem"
date: 2007-01-09
forum: Hardware &amp; Laptops
---

### Post by sk87 on 2007-01-09
Hi

I am aware that there are some problems with these cards but not sure this is the definatley problem or how to solve it.

I have an ATI mobility Radeon x700


when Ubuntu boots up (off a live cd) I can see the booting up screen bu when it comes it load the GUI then screen goes blank but the sound still works as I can hear the loading sounds.

I have tried different distros and all of them do exactly the same except for DSL which works.

My theory is that my ATI is not supported by GNOME or KDE but obviously does work for whaever DSL uses.

I hope i have explained this well and that you can help me. As you can ell im a linux newb.

Thanks

---

### Post by meng on 2007-01-09
There are a number of boot options you could try when the CD boots. I don't know the full list but one of the F-keys will give you a list. Look into the safegraphics, noacpi, noapic, nolapic options.

---

### Post by MueasA on 2007-02-23
I have the same problem, I tried booting from Graphics safe mode and it worked, but I didn't fine a solution to boot from normal mode. 

Any input regarding this issue is highly appreciated.

My sys. is:
Toshiba Satellite M70-193 
ATI mobility radeon x700 256MB
cintrino 2.13
80 GB HDD
512 DDR II RAM

Thank you in advance

---

### Post by dragonfly00 on 2007-03-08
had the same problem myself and found the solution here

[http://www1.chubb.wattle.id.au/PeterChubb/L715.html](http://www1.chubb.wattle.id.au/PeterChubb/L715.html)

basically you need to install ubuntu while connected to an external monitor.

Once installed then in the Device section of /etc/X11/xorg.conf and add

Option "MonitorLayout"  "LVDS,AUTO"

make sure you do a backup first :)

hope this helps.

---

