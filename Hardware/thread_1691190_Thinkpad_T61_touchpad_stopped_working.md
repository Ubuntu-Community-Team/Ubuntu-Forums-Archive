---
title: "Thinkpad T61 touchpad stopped working"
date: 2011-02-19
forum: Hardware
---

### Post by kvorion on 2011-02-19
I have had ubuntu 10.10 and windows7 dual boot on a laptop for some time now. My touchpad was working fine on ubuntu all this while, until I woke my laptop up from sleep yesterday and the touchpad was unresponsive on ubuntu. The two mousekeys adjoining the touchpad are also not working.

Interestingly the Systems->Preferences->Mouse settings does show touchpad as an option. I once restarted my machine after playing a little bit with these settings, and the touchpad was responsive, but it soon became unresponsive after a couple of seconds.

I know that this is not a hardware issue because the touchpad still works fine on windows7 and I did not change any settings/configurations on ubuntu that would make it stop working.

Any help/suggestions would be appreciated.

---

### Post by kvorion on 2011-02-20
bump. please help. 

update: as i was booting my machine into ubuntu, the touchpad started working for exactly 5 seconds, and then it became unresponsive again. i cannot figure out why this is happening.

---

### Post by kvorion on 2011-02-20
this fixed it:

Touchpad not working after login
This usually happens when you disable your touchpad and then suspend your computer. To fix this just run this command:


gconftool-2 --set --type boolean /desktop/gnome/peripherals/touchpad/touchpad_enabled true

---

### Post by sribalajee on 2012-01-24
I have a similar problem, but the suggested solution did not fix it.

one fine day the Lenovo T61's Touchpad and Stick mouse stopped working. 

External mouse works.

Have tried remove and re-install packages Gpointing devices and Gsynaptics.

Preferences > Touchpad gives the following error

Gsynaptics couldnt initialize
you have to set SHMCONFIG true in xorg.conf
or XF86config to use Gsynaptics


Tried creating Xorg.conf file in vain.

Please help

---

