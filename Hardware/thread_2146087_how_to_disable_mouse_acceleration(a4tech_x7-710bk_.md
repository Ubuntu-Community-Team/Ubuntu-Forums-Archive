---
title: "how to disable mouse acceleration?(a4tech x7-710bk + ubuntu 13.04)"
date: 2013-05-17
forum: Hardware
---

### Post by iiso on 2013-05-17
Good day. 

I'm not very friendly with english and I find it hard to describe the problem.

Tried to act instructions:
Terminal -> 
[COLOR=#000000][FONT=Ubuntu Beta]xinput --list --short
issues ->
[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Beta]&#9121; Virtual core pointer                       id=2   [master pointer  (3)][/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]&#9116;   &#8627; Virtual core XTEST pointer                 id=4   [slave  pointer  (2)][/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]&#9116;   &#8627; A4TECH USB Device                          id=8   [slave  pointer  (2)][/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]&#9116;   &#8627; A4TECH USB Device                          id=9   [slave  pointer  (2)][/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]&#9123; Virtual core keyboard                      id=3   [master keyboard (2)][/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]    &#8627; Virtual core XTEST keyboard                id=5   [slave  keyboard (3)][/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]    &#8627; Power Button                               id=6   [slave  keyboard (3)][/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]    &#8627; Power Button                               id=7   [slave  keyboard (3)][/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]    &#8627;   USB Keyboard                             id=10   [slave  keyboard (3)][/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]    &#8627;   USB Keyboard                             id=11   [slave  keyboard (3)][/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]    &#8627; Vimicro USB Camera (Altair)                id=12   [slave  keyboard (3)]
[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Beta]
[/FONT][/COLOR]**xinput --set-prop "A4TECH USB Device" "Device Accel Velocity Scaling" 1 - **to disable acceleration, 
[COLOR=#000000][FONT=Ubuntu Beta]show:
[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Beta]Warning: There are multiple devices matching 'A4TECH USB Device'.[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]To ensure the correct one is selected, please use the device ID, or prefix the[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]device name with 'pointer:' or 'keyboard:' as appropriate.[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Beta]
[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Beta]unable to find device A4TECH USB Device

[/FONT][/COLOR]On the laptop problems with Logitech mouse was not.

What is all this to me?
Even at the minimum sensitivity settings my cursor moves very quickly(minimum dpi). It is unusual for me.


Thank you for helping.
Thanks dismantled my gibberish

---

