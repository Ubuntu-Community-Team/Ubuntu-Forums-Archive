---
title: "ATI and HDTV resolution problems"
date: 2008-12-31
forum: Hardware
---

### Post by dzisler on 2008-12-31
How can I get the correct display resolution on 8.1. I have an ATI card using ATI Catclyst drivers for linux from ATI. In the menu from ATI it only shows a resolution as preferred and when picked is the resolution I need. It overrides the resolutions picked when going thru the menus (system, preferences, screen resolution). If I use an xterm window and run the command xrandr it only returns the current resolution from the screen resolution menu, not the true resolution. I need to find this out because the ATI preferred resolution needs to be reset every time the system is restarted.Once this is found what is the best way to make this change permanent.
Thanks

---

### Post by markbuntu on 2008-12-31
aticonfig has many options that are not avialable in the Catalyst Control Center.

You can find command options to do that by typing aticonfig --help in a termnal. To run the command you need to use sudo

sudo aticonfig --(option)

---

