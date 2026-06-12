---
title: "Toshiba 5200 PS522C-XK00EP backlight stays off after suspend to ram with s2ram"
date: 2007-08-05
forum: Hardware &amp; Laptops
---

### Post by realo on 2007-08-05
Hello world,

here is an informative post for those who would have a laptop similar to mine.

Laptop Description:
=============

cat /var/lib/acpi-support/bios-version 
Version 1.40

cat /var/lib/acpi-support/system-product-name 
Satellite 5200

cat /var/lib/acpi-support/system-version 
PS522C-XK00EP


The issue:
=======

The only thing that can do a correct suspend to RAM on this laptop seems to be the command "s2ram -f" from uswsusp package.  This works well, however the backlight does not come back after this.  

Te solution:
=======

Modify the following file:

/usr/lib/hal/scripts/linux/hal-system-power-suspend-linux

so as to remove most of the stuff not related to this laptop and replace it with the following lines:

sync && sync && sync
vbetool dpms off && s2ram -f && vbetool dpms on
rmmod ath_pci && modprobe ath_pci rfkill=0



The "sync" line might not be necessary, but one never sync's too much...

There are two tricks here.  First, it is not enough to call the "vbetool dpms on" by itself after s2ram comes back.  The dpms must be turned off manually first.  Since I have to turn off the backlight, might as well do it before the s2ram call, to avoid having to look at the text console while s2ram does its things.

Second, the atheros driver does not always come back properly.  Thus we force a reload, with "rfkill=0" to take care of the rfkill "bug".

With this you can now safely suspend, and come back.  I include my own suspend macro, if you wish to use it.  You should remove the .txt extension before you use it.

Lastly, be aware that there is a bug in gnome power manager:  suspending with the lid close switch does not work once in two times.  I workaround this one simply by using the "suspend" option offered when one left-clicks the small battery icon of the GPM.

Have a nice day...

Real

---

