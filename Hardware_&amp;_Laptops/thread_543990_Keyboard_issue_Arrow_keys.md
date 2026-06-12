---
title: "Keyboard issue: Arrow keys"
date: 2007-09-05
forum: Hardware &amp; Laptops
---

### Post by doctorbighands on 2007-09-05
I'm having an issue with three of my four arrow keys. I'm really, really hoping someone can help. I'll post whatever information is necessary on this thread for diagnostic purposes.

The down key functions properly; the others seem to be sending a signal, but they don't do what they're supposed to do (they don't do anything at all).

I ran xev. When I press down, it registers as a KeyPressEvent and KeyReleaseEvent, as I assume it should. When I press any of the other three, they register as FocusOut event, FocusIn event, and KeymapNotify event. This must be some sort of clue, but I don't know what it means.

Also, in System > Preferences > Keyboard, I tried the keyboard map. When pressing down, the corresponding orange key pops on. When pressing the other three keys, there is a definite signal, but the orange map keys don't light up.

I've only recently installed Ubuntu; when I was running Windows, all my keyboard functions were intact. The instant I switched to Ubuntu, I lost those three arrow keys. All other keyboard keys are still functional.

I'm stumped. Any ideas?

---

### Post by doctorbighands on 2007-09-14
*bump*

I'm still having this issue. Anyone?

---

