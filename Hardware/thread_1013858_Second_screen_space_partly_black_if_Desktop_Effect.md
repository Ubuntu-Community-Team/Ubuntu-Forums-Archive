---
title: "Second screen space partly black if Desktop Effects are enabled"
date: 2008-12-17
forum: Hardware
---

### Post by djst2 on 2008-12-17
Hi all,

I'm having a weird problem that I can't seem to figure out after googling and trying just about every setting there is, so I'm turning to you, the experts! :)

I have a MacBook Pro with a 15.4" screen (1440x900) which is connected to a 24" LCD screen (1920x1200) using a DVI cable. When connecting it, Ubuntu/Gnome properly detects the second screen and enables it with the native resolution (1920x1200) as a separate screen (not a clone of the first screen). All is working well when Desktop Effects is not enabled, and I can see both screens fully.

However, if I have Desktop Effects enabled, the screen space of the external screen is only partially rendered. It's still using the native resolution, but only part of it is drawn, and the rest is black. It looks like the part that's drawn corresponds pretty accurately to the 1440x900 resolution the laptop screen is using, but again, it's not a clone of that screen I'm looking at. 

Oh, and I can actually move the mouse cursor outside the rendered area, and the mouse cursor will actually be shown, but still with the black void around it. 

Any ideas what could be causing this? Since the NVidia driver properly detects two screens and uses the correct resolutions, and it works well without Desktop Effects, I'm guessing this is some sort of compiz or graphics card issue.

---

