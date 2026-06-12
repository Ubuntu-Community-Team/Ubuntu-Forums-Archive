---
title: "ATI x300 1024x768 only working resolution"
date: 2007-04-08
forum: Hardware &amp; Laptops
---

### Post by vortmax on 2007-04-08
I have a dapper install on a Dell I6000 with the ATI x300 video card.  The LCD works fine, but is running at 1024x768.  The native resolution for this display is 1280x800, but every time I set the resolution through the 'screen resolution' tool, it ends up displaying weird.  The far right of the screen is just a mirror of the far left, like it is wrapping around.

I haven't gone into the xorg config files yet.  Any suggestions?

---

### Post by heimo on 2007-04-08
> **vortmax said:**
> 
I haven't gone into the xorg config files yet.  Any suggestions?

Haven't heard before that LCDs do that. Anyway, I'd probably try running xvidtune to see if I could move it left/right and output a custom modeline for xorg.conf.

---

