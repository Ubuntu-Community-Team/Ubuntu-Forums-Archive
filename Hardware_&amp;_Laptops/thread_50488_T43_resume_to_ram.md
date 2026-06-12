---
title: "T43 resume to ram"
date: 2005-07-20
forum: Hardware &amp; Laptops
---

### Post by shizow on 2005-07-20
i cannot get to work suspend to ram with my t43 with sonoma chipset

there is a solution on this website
[http://www.thinkwiki.org/wiki/How_to_make_ACPI_work](http://www.thinkwiki.org/wiki/How_to_make_ACPI_work)

but can anyone give a newbie a hint
how do i apply a kernel patch which looks like this
[http://shamrock.dyndns.org/~ln/linux/sata_pm.2.6.12.diff](http://shamrock.dyndns.org/~ln/linux/sata_pm.2.6.12.diff)

---

### Post by emperor on 2005-07-20
ourbox:~ # cd /usr/src/linux
             yourbox:/usr/src/linux # patch -p1 < /path/to/yourpatch.diff

Note: /usr/src/linux is a symlink to your kernels source directory.

This guy has a T43 and has documented his success with Debian/Ubuntu

[http://meltin.net/hacks/linux/t43.html]("http://meltin.net/hacks/linux/t43.html")

He used got suspend to disk working with the patches from here:
[http://www.suspend2.net/]("http://www.suspend2.net/")

Older patches for older kernels are here:
[http://www.suspend2.net/downloads/all/]("http://www.suspend2.net/downloads/all/")

---

