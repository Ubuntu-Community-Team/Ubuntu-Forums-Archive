---
title: "brightness in sony vpccw1mfx"
date: 2012-05-06
forum: Hardware
---

### Post by ghiasi on 2012-05-06
The brightness control are not working on Ubuntu 12.04 32-bit  , Sony Vaio VPCCW.
 I've tried both ways Fn + F5 / F6 and from Brightness/Lock menu (under  Settings)
but nothing  changes so it looks like the brightness controls are not working at all.
  Anyone know if there is a workaround for this ?

](*,)](*,)](*,)](*,)](*,)](*,)](*,)](*,)

---

### Post by animesh271094 on 2012-05-06
Having the same problem. Though mine is a 64-bit HP pavilion. :/
The brightness in Ubuntu dont seem to work at all

---

### Post by chrs on 2012-05-18
I have a Sony VPCCW26FX with the same issue and this is what worked for me:

First backup your grub config
> sudo cp /etc/default/grub /etc/default/grub.backupThen open up /etc/default/grub and change the two lines to this:
> 
  GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=sony" 

GRUB_CMDLINE_LINUX="acpi_osc=Linux"

Then run
> sudo update-grubThen restart.


If it still doesn't work add this to the Device Section of /etc/X11/xorg.conf if it's not already there.
> 
  Option  "RegistryDwords"    "EnableBrightnessControl=1"

---

