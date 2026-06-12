---
title: "HP w1907v monitor and Resolutioin setting"
date: 2007-07-29
forum: Hardware &amp; Laptops
---

### Post by hopefull on 2007-07-29
Hi

In a previous post I said I was having problems getting this new monitor to work at 1440/900. Through much trying I am now at a point where I can get the monitor resolution to be set at this figure, but the quality of reproduction is much less than running it at 1280/800 and the desktop is slightly bigger than the monitor.
I am using Ubuntu feisty fawn 64, using KDE as the desktop. I have a Radeon Pro 9250. I have set the monitor and display as follows;
- Graphics card: ATI
- Driver: ATI
- Monitor one: Generic 1440x900
- monitor two: generic 1440x900
-screen size set to: 1280x800
I have tried all sorts of combinations, radeon instead of ATI, HP driver for a 20.2 LCD - the monitor is new so ubuntu do not have the drivers-. But this is best.
However, if i log out to the log out screen and then lick on the icon to get up the menu for shutdown, etc my screen goes all funny lots of lines looking very nasty. This does not happen when I shut down from KDE.
I have two questions;
- when the screen goes nasty at log out, does this mean that this combination of setting is doing damage to the monitor?
- is this the best combination to use? After loging in the monitor says it is making automatic adjustments to 1440x900: does this mean that monitor is setting itself to 1440x900 despite the above settings?
This is a lovely monitor and the picture quality is excellent and thus I do not want to do damage to it, but I do want to set it at the optimum settings (which under windows is 1440x900, but the HP also comes with windows software to set the exact colours etc). Can anyone help, please?

hopefull

---

### Post by hopefull on 2007-07-29
Hi

I appear to have solved this problem. I reconfigured x-oxg thus

Drivers ATI
Resolution: 1440x900
Set the Horizontal freq at 24-83
vertical   50-76

restarted. In system setup- changed the driver from ATI to Radeon- set the screen resolution as 1440x900, set monitor to generic flat panel1440x900 and  set the monitor to work as widescreen (which I think is the magic ingredient)  and rebooted. And now it appears to be working.

---

