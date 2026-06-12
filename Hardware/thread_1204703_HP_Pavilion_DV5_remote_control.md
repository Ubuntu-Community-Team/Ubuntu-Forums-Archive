---
title: "HP Pavilion DV5 remote control"
date: 2009-07-05
forum: Hardware
---

### Post by dr_doom on 2009-07-05
Ubuntu Jaunty 9.04 with kerenel 2.6.30
I want to remap the keys of the remote control because a single button press produce three different keycodes.
When I issue showkey -k I see the following output:

keycode  29 press
keycode  42 press
keycode  48 press
keycode  48 release
keycode  42 release
keycode  29 release

When I issue shokey -s and press the same button I see the following output:
0x1d 0x2a 0x30 0xb0 0xaa 0x9d

How can I map the scancode to a single keycode?
The syntax for setkeycodes is to use a single scan code number, but in my case I have "0x1d 0x2a 0x30 0xb0 0xaa 0x9d"
Also I see no output in dmesg when I press any of the keys which are not mapped.

---

