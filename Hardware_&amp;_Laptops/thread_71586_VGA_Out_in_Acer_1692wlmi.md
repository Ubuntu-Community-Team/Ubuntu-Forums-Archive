---
title: "VGA Out in Acer 1692wlmi"
date: 2005-10-03
forum: Hardware &amp; Laptops
---

### Post by Chillout on 2005-10-03
Hello.
I need to use my laptop for presentations, but I can't get it to use the vga out. In Windows all works fin e. But in Ubuntu, the button to change the display from lcd to vga (or both at the same time) doesn't work.
I am using the default drivers that came installed with Ubuntu, not the real ATI ones.

BIOS has 2 options regarding this: power up with both graphic devices outputing, or detecting at boot up who's working automatically. I get mixed results:
 
- BOTH: BIOS' POST looks fine, I can see the ubuntu graphical boot up fine in the laptop's lcd and in the monitor. But the one in the monitor has a weird resolution, as in showing only 90% of the screen. The ubuntu graphical boot up is at default resolution. In X I have 1280x800, but when boot up ends and GDM starts, the monitor shuts down, and I can only see the screen at the LCD.

-AUTOMATIC: The Monitor starts as the only display showing. All is fine untill GDM. In that time the monitor shuts down, and the LCD powers up, but all is black. That blackness reminded me of the blackness I had after installing ubuntu and having to add to /etc/X11/xorg.conf the Option "MonitorLayout" "LVDS,TMDS". I can hear sound, but no display.

Anyone has any idea? Please help... i didn't want to go back to windows to be able to do my presentations.

---

