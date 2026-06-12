---
title: "HP TX2500 Touchpad disabled"
date: 2010-05-09
forum: Hardware
---

### Post by Drycola on 2010-05-09
Hello,

I have HP TX2500 running ubuntu 10.04. One day I accidentally pressed the touchpad-disable button (which is found just above the touchpad in most hp laptops) since then the touchpad is disabled for good!
Then I've realized that the touchpad works properly at the login screen but once I log into my account it stops working.
I made another user account and the touchpad works normally in the new account!!

I guess the problem is in the X.org but I don't even know where to find the configuration file for X server in Lucid!

Any suggestions??

---

### Post by Drycola on 2010-05-09
No answers!
Is my issue too complicated?? Or it is just because I was too specific???
At least tell me where to find the configuration file for X!!!

Sorry but I'm a little frustrated with my annoying problem.

---

### Post by Favux on 2010-05-09
Hi Drycola,

Well I can tell you where the configuration files are.  The new .conf files are at /usr/lib/X11/xorg.conf.d/.  They're what replace the .fdi files.  The xorg.conf is in the same place  /etc/X11/.

---

### Post by Drycola on 2010-05-09
Is there a specific configuration file for each user?? or it is a shared file?
If it is a shared file, so what is making my first account defective while the second account have no problem with the touchpad??

---

### Post by Favux on 2010-05-09
Good questions.  I don't know for sure.  I think they're shared.  But before you go comparing the synaptic.conf's I'd check Mouse Preferences in Preferences and make sure that under Touchpad you have Enabled touchpad checked.

---

### Post by sukigenseki on 2010-10-25
I just picked up a tx2510, and on lucid the touchpad works just fine, but under 10.10 only the wacom screen works for input. The touchpad is a synaptics pad, and if anyone has any ideas where to start to try to figure out what's causing this I'd love the help.

---

