---
title: "Toshiba Satellite S2450-201 &quot;at&quot; key- problem after upgrading to Feisty"
date: 2007-04-21
forum: Hardware &amp; Laptops
---

### Post by Lizzy on 2007-04-21
Where did the "at" button go ???  :) 

Hi everyone, i'm the proud owner of an "old" Toshiba Satellite who has worked fantastic with Ubuntu until yesterday :-D. I don't know if this is a known bug, but 1 button on my (norwegian) keyboard stoped working :confused: The "at" button, in other words.... I can't write an email :lolflag:  I tried all sorts of keycombinations but none works. I tried to change the layout, but nothing works...** Everything else works just perfect **with Feisty, which suprised me..

Any help would be appreciated, cause i don't wanna switch back to Edgy because of **1 BUTTON**  :lolflag: 

[B]
Error message:[/B]

Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
70200000

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd

**Another output:**


elisabeth@elisabeth-laptop:~$ Reply With Quote:~$ xprop -root | grep XKB
_XKB_RULES_NAMES_BACKUP(STRING) = "xorg", "pc105", "no", "no", "lv3:ralt_switch"
_XKB_RULES_NAMES(STRING) = "xorg", "pc105", "no", "no", "lv3:ralt_switch"
elisabeth@elisabeth-laptop:~$ gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd
 layouts = []
 model = 
 overrideSettings = true
 options = []




Cheers Elisabeth :-))


Edit:  Caugh: It seems that all "AltGr" buttons don't work on my laptop, and that trying to configure the keyboard only results in error-messages like the 1. one i've posted :-( 

Bump :-)

Kernel upgrade necessary? One might ask?

---

### Post by Lizzy on 2007-04-22
Since i found no solution by tweaking around, i did a fresh install. Now all keys work fine :-D .

---

