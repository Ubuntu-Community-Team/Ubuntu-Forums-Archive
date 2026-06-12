---
title: "Thinkpad 600X hibernate/standby problem"
date: 2006-02-17
forum: Hardware &amp; Laptops
---

### Post by the_djr on 2006-02-17
Hi all,

I have installed Breezy and the latest updates onto a Thinkpad 600X and it all seems to work OK except for hibernate and standby.

I can't wake it is up after standby. (The only thing I can do to get it working is the power switch which just boots from scratch).

After hibernate everything seems to work - but very, very slowly.

I have set my kernel options to acpi=off apm=on and removed splash.

Any ideas anyone? Thanks in advance for any help.

---

### Post by the_djr on 2006-02-19
Hmmmm, found this via google - it sounds like no fdd is my problem.

[http://www.thinkwiki.org/wiki/How_to_make_APM_work#Troubleshooting](http://www.thinkwiki.org/wiki/How_to_make_APM_work#Troubleshooting)

Does anyone know what this modprobe malarky is???

(So much for ubuntu being user friendly .....:( )

---

### Post by borris.morris on 2007-02-12
I set my kernel options to acpi=force pci=noacpi and all works well.

---

