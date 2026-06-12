---
title: "Wireless Keyboard and mouse makes screen flash"
date: 2009-03-25
forum: Hardware
---

### Post by SteveNorman on 2009-03-25
I have a logitech ex100 wireless keyboard and mouse combe. It works, but in gnome my applications flash off and back on( ex when I type this periodically the desktop flashes in view for a fraction of a second).

This only happens in gnome, when I log into my fluxbox session there is no problem of any kind. 

I am using compiz with all the bells and whistles, and no I do not want to turn off compiz as that is the only reason I ever use gnome. Driver is an Nvidea 177.82


does anyone have a xorg.conf entry for this? Or any other ideas what the problem is?

---

### Post by utnubuuser on 2009-03-25
had an issue with screen flashing at one point.  - had to change the refresh rate from 70 to 75 or vice versa.
sometimes xorg sets it to 60 instead of 65 or something similar.  try adjusting your refresh rate.

---

### Post by SteveNorman on 2009-03-26
Ill, have to try that...

---

