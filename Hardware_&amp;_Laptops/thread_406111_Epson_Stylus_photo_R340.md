---
title: "Epson Stylus photo R340"
date: 2007-04-10
forum: Hardware &amp; Laptops
---

### Post by loserboy on 2007-04-10
Ok, I installed edgy on my computer at work that has a epson R340 attached to it, and it was working fine under dapper.

I followed this howto [http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-Stylus_Photo_R340](http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-Stylus_Photo_R340)

and it acts like it should work, it's recognized, it shows i have the gutenprint driver too, but when i try to send a page to it, it shows sent then in the jobs window it shows stopped.

I tried re-installing the gutenprint drivers but I get this message, i don't remember getting this error the 1st time it installed.

```

(Reading database ... 115142 files and directories currently installed.)
Preparing to replace gutenprint 5.0.0.99.1-2 (using .../gutenprint_5.0.0.99.1-2_i386.deb) ...
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
dpkg: error processing /home/mike/Desktop/gutenprint_5.0.0.99.1-2_i386.deb (--install):
 subprocess new pre-removal script returned error exit status 1
 * Restarting Common Unix Printing System: cupsd                         [ ok ] 

```

I really need this up and running so any help woul be appreciated.

---

### Post by loserboy on 2007-04-10
oops false alarm, I tried one more thing and it worked, I went to the package manager and re-installed everything through that and it worked

---

