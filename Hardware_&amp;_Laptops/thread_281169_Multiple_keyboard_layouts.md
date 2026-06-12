---
title: "Multiple keyboard layouts"
date: 2006-10-20
forum: Hardware &amp; Laptops
---

### Post by LeslieL on 2006-10-20
I want to be able to use both Turkish and US English keyboard layouts. When I try to change it in Ubuntu using System > Preferences > Keyboard > Layouts I get 
> Error activating XKB configuration.
This can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
70000000

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd

The result of xprop -root | grep XKB is 
> _XKB_RULES_NAMES_BACKUP(STRING) = "xorg", "pc104", "us", "", ""
_XKB_RULES_NAMES(STRING) = "xorg", "pc104", "us", "", ""


The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd is
>  layouts = [us]
 model = presario
 options = [grp grp:alts_toggle]
 overrideSettings = false


I tried using setxkbmap: setxkbmap -v -layout "us,tr" 
> Warning! Multiple definitions of keyboard layout
         Using command line, ignoring X server
Trying to build keymap using the following components:
keycodes:   xfree86+aliases(qwerty)
types:      complete
compat:     complete
symbols:    pc(pc104)+us+tr:2
geometry:   pc(pc104)
Error loading new keyboard description


I'm using Ubuntu Dapper with the latest everything on a Compaq nx7010 laptop. 

I have looked at everything in this forum referencing XKB and googled everything I can think of. Nothing has helped.

Any helpful ideas?

---

### Post by LeslieL on 2006-10-20
Okay, I've kinda got it working. I looked again through everything on this forum that mentions XKB and looked again at a bug report, [https://launchpad.net/distros/ubuntu/+source/xkeyboard-config/+bug/21595](https://launchpad.net/distros/ubuntu/+source/xkeyboard-config/+bug/21595). One response suggested downloading and installing xkeyboard-config_0.6-6_all.deb. I couldn't install it because it's older than the current version, but I noticed that it had more files in its /etc/X11/kbd folder than I had in mine. So I renamed my existing  /etc/X11/kbd folder and extracted the ones I'd downloaded to a new kbd folder. Now it works. I can use System > Preferences > Keyboard > Layouts to change layouts without a problem, and setxkbmap works without a problem. So it looks like the newest xkeyboard-config is faulty.

---

