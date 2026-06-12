---
title: "keyboard problems"
date: 2006-11-05
forum: Hardware &amp; Laptops
---

### Post by bgalan on 2006-11-05
greetings to all. i love ubuntu (and kubuntu and xubuntu). i tried to install a keyboard map to be able to write hebrew with vowels (nekudim). i wasn't able to do it and, in the process, my keyboard changer was broken. now every time i boot in i get this miserable message:

Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
70101000

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd


the answers provided elsewhere in this forum, or anywhere else, haven't worked so far. one person simply suggested to re-install the system (which i'd like to avoid, if possible).

i work in three different languages and i really need to be able to change my keyboard back and forth frequently. so, until i fix this (which was working beautiful before), ubuntu is but a toy for me.  agh! back to windows for now! ](*,) 

any help would be greatly appreciated. This is the input from the xprop and gconftool commands:

bgalan@eved:~$ xprop -root | grep XKB
_XKB_RULES_NAMES_BACKUP(STRING) = "xorg", "ze4xxx", "us,latam,il", "", "grp:Alt_shift_toggle,grep_led:scroll"
_XKB_RULES_NAMES(STRING) = "xorg", "ze4xxx", "us,latam,il", "", "grp:Alt_shift_toggle,grep_led:scroll"
bgalan@eved:~$ gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd
 layouts = [us,latam,il si1452]
 model = pc104
 options = [grp grp:Alt_shift_toggle,grep_led   grep_led:scroll]
 overrideSettings = false


thanks!
benjamin

---

### Post by bgalan on 2006-11-09
any help, anyone? please, please, please... i'm surviving, barely, with windows, but i'm not enjoying it ;) 
thanks in advance
benjamin

---

