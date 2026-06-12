---
title: "Animated Desktop"
date: 2008-09-08
forum: General Help
---

### Post by k33bz on 2008-09-08
I am running Ubuntu Hardy 8.04LTS, gnome and compiz-fusion. When I run this script:```
#!/bin/bash


# Animated Desktop v0.3 by r0ot
# 2008 - bash
# elteter0ot@gmail.com


#kill any process xwinwrap
killall xwinwrap


#launch xwinwrap with mplayer with any videos (no sound and loop)
xwinwrap -ni -o 1.0 -fs -s -st -sp -b -nf -- mplayer -wid WID -quiet -nosound ~/animated_desktop/killertux.avi -loop 0 &

#~/animated_desktop/tren.avi
#~/animated_desktop/chaostheory.avi
#~/animated_desktop/spiritheory.avi
#~/animated_desktop/Horaktartz.avi
#~/animated_desktop/George_Washington.avi
#~/animated_desktop/Energy_Field_by_Snowmanzors.divx
#~/animated_desktop/locemotion.avi
#~/animated_desktop/wraith3d.avi
#~/animated_desktop/skulls.mpg
#~/animated_desktop/glassthing.mpg




#launch xwinwrap with any screensavers
#xwinwrap -ni -argb -fs -s -st -sp -nf -b -- /usr/lib/xscreensaver/hufo_tunnel -window-id WID &

#/usr/lib/xscreensaver/glmatrix
#/usr/lib/xscreensaver/fiberlamp
#/usr/lib/xscreensaver/blinkbox
#/usr/lib/xscreensaver/hufo_tunnel


```


When I run this script my screen just turns blue, almost like the blue screen of death, and it is unresponsive.  
Any ideas?

---

### Post by k33bz on 2008-09-10
Bump

---

