---
title: "Adjust Touchpad Dimensions"
date: 2011-04-03
forum: Hardware
---

### Post by RudyWithNoD on 2011-04-03
Hello,
I would like to be able to adjust the dimensions of my touchpad.  I have a lenovo y560 and often I will slightly brush my palm against the touchpad while typing.  

I have already enabled the "disable touchpad while typing" option in gnome.  This has helped some, but it would be nice to also adjust the delay between the last key pressed and when the touch pad is renabled.

I also would like to determine how I can enable the lenovo function key fn+F6 to toggle the touchpad on/off.  I know I use touchpad-indicator, but that is ctl+alt instead of a quick fn+F6.  But this is tertiary.  If someone can tell me where the touchpad dimensions, and typing delay are set, I think that will solve the problem.

Gnome 2.32 
Ubuntu 10.10
uname -a: Linux tesla 2.6.35-28-generic #49-Ubuntu SMP Tue Mar 1 14:39:03 UTC 2011 x86_64 GNU/Linux

---

### Post by RudyWithNoD on 2011-04-03
synclient PalmDetect=1 
and
syndaemon -i 0.7 -d -K //make sure to kill previous instances of syndaemon first via kill -9 `pgrep syndaemon`

have helped somewhat, but adjusting the dimensions would be ideal.  The syndaemon command above disables the touch pad for .7s while typing.  


-d daemonize 
-K do not disable for key combinations.  (I might turn this off because I think it is leaving the trackpad on when I hit the shift key.

---

