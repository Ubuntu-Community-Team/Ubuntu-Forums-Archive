---
title: "Multimedia keys stop working after reboot."
date: 2010-11-14
forum: Hardware
---

### Post by Vu1kan on 2010-11-14
My particular issue is with the multimedia buttons on my usb internet keyboard: whenever i reboot/power down, they stop working.  In gnome-keybinding-properties, it shows the various actions are defined correctly, i.e. volume mute is mapped to XF86AudoMute, but i get nothing if i press any of the buttons that were previously defined.
The only way i've been able to 'fix' this is to first clear the actions with backspace, then redefine the shortcut with the appropriate media button.  It's getting rather tiresome to have to run the keybinding utility every time i reboot.
It only seems to affect the XF86foo buttons, because Mod4+t always opens a terminal for me.  I investigated keytouch, but it doesn't seem to do anything more than the gnome keybinding utility.
:confused:

---

### Post by Vu1kan on 2010-11-15
*bump*
and
I tried reassigning the volume shortcuts-up, down and mute-to alt+num plus, alt+num minus and alt+num asterisk, and those shortcuts function after a reboot...so my issue is definitely the XF86foo buttons.

Just in case it helps, my volume mute/up/down, next track, play/pause, previous track, and stop buttons all have the following keycodes/keysyms defined in xmodmap: 121 0x1008ff12 (XF86AudioMute) 0x0000 (NoSymbol) 0x1008ff12 (XF86AudioMute); 122 0x1008ff11 (XF86AudioLowerVolume) 0x0000 (NoSymbol) 0x1008ff11 (XF86AudioLowerVolume); 123 0x1008ff13 (XF86AudioRaiseVolume) 0x0000 (NoSymbol) 0x1008ff13 (XF86AudioRaiseVolume); 171 0x1008ff17 (XF86AudioNext) 0x0000 (NoSymbol) 0x1008ff17 (XF86AudioNext); 172 0x1008ff14 (XF86AudioPlay) 0x1008ff31 (XF86AudioPause) 0x1008ff14 (XF86AudioPlay) 0x1008ff31 (XF86AudioPause); 173 0x1008ff16 (XF86AudioPrev) 0x0000 (NoSymbol) 0x1008ff16 (XF86AudioPrev); 174 0x1008ff15 (XF86AudioStop) 0x1008ff2c (XF86Eject) 0x1008ff15 (XF86AudioStop) 0x1008ff2c (XF86Eject).  Additionally, keycodes 208 and 215 both have XF86AudioPlay connected to them.

i have no idea where to even start troubleshooting:frown:

---

