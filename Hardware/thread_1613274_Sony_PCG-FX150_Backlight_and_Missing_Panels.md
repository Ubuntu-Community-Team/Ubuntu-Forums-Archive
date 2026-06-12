---
title: "Sony PCG-FX150 Backlight and Missing Panels"
date: 2010-11-04
forum: Hardware
---

### Post by chris1379 on 2010-11-04
Sony PCG-FX150
PIII 750MHZ
512MB RAM
Intel 815 graphics

I originally had problems with the resolution stuck at 800 x 600 but solved that by reading the forums. I have tried setting the backlight to go off after 5 or 10 minutes but it won't work. The display blanks but the backlight stays on. I can control the brightness with hotkeys and it dims when on battery but it won't go off. Issuing the command ```
xset dpms force off
``` doesn't work either.

Sometimes the top and bottom panels are missing from the desktop. Pressing Alt+F2 and ```
killall gnome-panel
``` will cause them to show up.

---

### Post by P4man on 2010-11-04
Does your bios have options for DPMS ? If so, experiment with the settings.

If that doesnt help, you might try booting with acpi_osi= boot parameter, see my signature.

For the panels not loading, have a look in your log files (syslog) at around the time you logged in, and see if that sheds any light on the issue.

---

### Post by chris1379 on 2010-11-05
> **P4man said:**
> Does your bios have options for DPMS ? If so, experiment with the settings.

If that doesnt help, you might try booting with acpi_osi= boot parameter, see my signature.

For the panels not loading, have a look in your log files (syslog) at around the time you logged in, and see if that sheds any light on the issue.

Thanks for the help. I don't see any DPMS options in BIOS. I tried acpi_osi= and several other options but with no luck (if I even put them in the right place). I'm beginning to think the backlight is controlled separately from the LCD. It seems like Ubuntu doesn't know the display is part of the laptop. I wonder if laptop-mode tools would do the trick.

As for the panels, I don't see anything odd in syslog. Occasionally they actually work. I also have a problem with the computer not shutting off. It goes through the shutdown procedure but stays on with the caps lock and num lock flashing.

---

### Post by chris1379 on 2010-11-07
I solved my missing panels by changing desktop themes. Anything other than Ubuntu's default theme works just fine. However, I'm getting really frustrated at the backlight issue. A laptop really needs to be able to turn off the backlight to save power. It works fine in Windows with no special setup at all. Can someone tell me where to start? Something in Xorg.conf, maybe? Anyone have a similar laptop that turns off the display backlight completely? The odd thing is I can dim it manually or automatically in Power Management but I can't turn it off. Argh!!!

---

