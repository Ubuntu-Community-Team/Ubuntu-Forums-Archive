---
title: "Fan control on Thinkpad T4x"
date: 2005-10-14
forum: Hardware &amp; Laptops
---

### Post by stevetxt on 2005-10-14
Does anyone know how to control the fan on a Thinkpad T4x?   I have a T43 but I think this affects all the T4x series.  The fan seens to run all the time, even when the computer is doing very little.

Thanks.

Steve

---

### Post by Jingo on 2005-10-14
[QUOTE=stevetxt]Does anyone know how to control the fan on a Thinkpad T4x?   I have a T43 but I think this affects all the T4x series.  The fan seens to run all the time, even when the computer is doing very little.

Thanks.

Steve[/QUOTE]

The bios is taking care of the fan.
You should take care of the heat produced. Enable powersaving.
CPU scaling is by default done by powernowd.
rovclock can be used to underclock the gfx-card.

thinkwiki.org is your friend!

---

### Post by pepeke on 2005-12-01
maybe your friend but not a truly correct one

check out 
[http://ubuntuforums.org/showthread.php?p=534981#post534981](http://ubuntuforums.org/showthread.php?p=534981#post534981)
howto buil acpi_ibm (first download source of course)

you need to rebuild acpi_ibm because experimental=1 in ubuntu doesn't seem to work for me (2.6.12-10-686)

then enable disable fan is as easy as echo enable > fan ...

take care not to burn the family jewels (and your tp) of course ;-)

cheers

---

