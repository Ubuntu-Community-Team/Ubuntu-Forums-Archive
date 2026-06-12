---
title: "Multi-monitor in ATI (Radeon 3450 + 790GX).  Can't use all of secondary monitor!"
date: 2009-08-03
forum: Hardware
---

### Post by GeekLove_JavaStyle on 2009-08-03
Hello All,
I have 2 monitors with Xinerama, but am having a strange issue.  I have a 1600x1200 primary monitor on the left and a 1920x1200 monitor on the right.  I can't use the full display on the secondary/right-hand monitor.  When I drag a window to the right and maximize it, I can't access the right 3rd or so of the screen.  It's just the background orange color and I can't move the window into it.  The maximized window also overlaps into the primary monitor's space.  

I have a 790GX embedded graphics card and a Radeon 3450 card.  
Here's my experience:
[LIST]
[*]distribution proprietary driver + 790GX + 3450:  no xinerama.
[*]distribution proprietary driver + 3450 only:  no xinerama.  (I disabled the embedded graphics in the BIOS).
[*]latest driver from ATI + 3450 only:  xinerama, but buggy display.
[*]latest driver from ATI + 790GX + 3450 only:  xinerama, but buggy display.
[/LIST]

Is there a setting in catalyst that'll fix this?  I didn't see anything obvious or related to offsets in my xorg.conf.  

Is there a common name for the bug I'm facing?  I'm having a hard time googling it as it's hard to describe.  I'm sure I'm not the only guy who's ever experienced it.  

Has anyone gotten dual monitors to work with ATI graphics in a similar configuration?

Thanks in advance,
Steven

---

