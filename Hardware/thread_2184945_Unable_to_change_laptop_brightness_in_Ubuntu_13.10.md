---
title: "Unable to change laptop brightness in Ubuntu 13.10"
date: 2013-10-31
forum: Hardware
---

### Post by x6herbius on 2013-10-31
I have recently installed Ubuntu on a Clevo P150SM and am unable to change the screen brightness either by the function buttons or in the brightness and lock section of Ubuntu settings, which ends up being a little taxing on my battery. I have seen solutions suggested as the following:

- Adding "acpi_backlight="vendor" (or something close to this) on the GRUB command line - didn't work for me.
- Changing settings in xorg.conf - I don't have this because I don't currently have graphics drivers above the Ubuntu default. I have an NVidia GTX 770M which uses Optimus and the current NVidia drivers appear to boot me to a black screen with the mouse cursor after I log in. I have also tried Bumblebee but optirun reports a missing GLAPI symbol when executed, so I've gone back to the default drivers for now. While running Bumblebee I didn't see the brightness slider appear in the brightness and lock settings.

Is there a way to fix this? Pointers with respect to the graphics drivers would also be appreciated.

Thanks.

---

