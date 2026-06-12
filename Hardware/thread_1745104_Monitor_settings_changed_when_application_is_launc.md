---
title: "Monitor settings changed when application is launched."
date: 2011-04-30
forum: Hardware
---

### Post by ceduardo.melo on 2011-04-30
I have an HP Dm3 notebook, with ATI Radeon 3200 HD video card with a second monitor plugged in the VGA port. In my settings, the laptop display is turned off.

After upgrading to Natty, my desktop began to have an strange behaviour. When I launch some applications (for now, I've seen this behaviour with Shotwell, Exaile and QuodLibet), my monitor settings are changed.

When I launch Shotwell, the screen is cloned in both monitors, ie, the monitor settings are changed to clone the screen in both monitors with a resolution of 1024x768.

The other two applications (Exaile and QuodLibet), when launched, changes the monitor settings to extend the screen to fill both monitors, and the LVDR display is set as the primary display.

I tried to use the proprietary drivers from ATI site, repository drivers, and open source driver (in this order) but none solved my problem. Does anyone know what might be causing this?

EDIT:

For those seeking an answer:

After reading [this site]("http://www.jejik.com/articles/2008/10/setting_up_dual_monitors_system-wide_with_xrandr_on_debian_lenny/"), I learned that there is a plugin in gnome_settings_manager that tries to get the best xrandr configuration for the current monitor setup. It turn out that was this plugin the source of my headaches. All you have to do is disable it in gconf-editor at /apps/gnome_settings_manager/plugins/xrandr by unchecking the "active" box.

---

