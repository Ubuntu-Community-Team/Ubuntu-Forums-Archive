---
title: "Right alt mapped as alt-gr aka level 3 switch"
date: 2009-10-30
forum: Hardware
---

### Post by michael37 on 2009-10-30
(repost from closed forum)

By default, my Karmic 9.10 installation configured "Right Alt" key mapped to Alt-Gr functionality aka ISO_Level3_Shift.

Given the changes in Karmic, I don't even understand if the binding happens in gnome, in udev, or somewhere else.

For some people, having level 3 switch might be interesting. I have a simple US keyboard and I don't have third level keys, so I don't care for Alt-Gr. I just want my Right Alt be Right Alt. How can I do that?

xev tells me that:
'Right alt
keycode 108 = (keysym 0xfe03, ISO_Level3_Shift), state = 0x0
keycode 108 = (keysym 0xfe03, ISO_Level3_Shift), state = 0x80
'Left alt
keycode 64 = (keysym 0xffe9, Alt_L), state = 0x0
keycode 64 = (keysym 0xffe9, Alt_L), state = 0x8

---

