---
title: "Is there a way to turn off all flashy compiz effects?"
date: 2008-08-08
forum: General Help
---

### Post by shjoity on 2008-08-08
Is there a way to turn off all flashy compiz effects? I like the extra window management functions but cant stand the stomach turning animations--i hate pointless animations and bloat. It there a way to tuen off all animations? Also i cant find any global opacity control/switch.

---

### Post by Patricrawley on 2008-08-08
system>prefrences>advanced desktop settings

all the settings can be found there.

if not sudo apt-get install fusion-icon and access the settings menu that way.

---

### Post by shjoity on 2008-08-08
i could find above settings there

---

### Post by loligager on 2008-08-08
Simple dude
System prefrences apperances [go to the last tab and select none]
AND you are braking my heart... I LOVE COMPIZ

---

### Post by shjoity on 2008-08-08
i have it back at none. i like compiz but i just want it without its animations. It provides alot of stuff that isnt flash, and i want only that. Its configuration doesnt seem to offer that option

---

### Post by mtbsoft on 2008-08-08
There isn't a *single* option marked "enable/disable flashy bits" other than disabling compiz altogether.  

Sounds like you might need to install ccsm (the compiz manager) and selectively turn on/off the various special effects one by one until you find the mix you can live with.

---

### Post by shjoity on 2008-08-08
yeah but compiz overwrites alot of stuff and, for example, if you disable work-space effects you cant switch with the gnome-panel switch anymore (only ctrl-alt left/right)

---

### Post by DaymItzJack on 2008-08-08
To extend on that:

```
sudo apt-get install compizconfig-settings-manager
``` in terminal and then go to System -> Preferences -> CompizConfig Settings Manager (or type 'ccsm' in terminal) and disable all the options you don't want, like 'wobbly windows' or 'desktop cube'/'rotate cube', and everything that you deem "flashy".

---

