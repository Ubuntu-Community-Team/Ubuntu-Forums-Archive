---
title: "Keyboard trouble, xorg"
date: 2008-10-01
forum: Hardware
---

### Post by madssakre on 2008-10-01
Hi

I'm trying to get my danish keyboard to work but I sense that many have the same problems regardless the language. 
Apparantly it' is the XKB something:
---------------------------------------------------------
Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
10400090

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd
---------------------------------------------------------

so I get:

---------------------------------------------------------
_XKB_RULES_NAMES_BACKUP(STRING) = "xorg", "pc105", "dk", "dk", ""
_XKB_RULES_NAMES(STRING) = "xorg", "pc105", "dk", "dk", ""
---------------------------------------------------------

and

---------------------------------------------------------
layouts = []
 model = inspiron
 overrideSettings = true
 options = []
---------------------------------------------------------

I have tried:

sudo dpkg-reconfigure xserver-xorg


MANY times!

Still no luck

Has anyone solved it?

Regards

Madssakre

---

