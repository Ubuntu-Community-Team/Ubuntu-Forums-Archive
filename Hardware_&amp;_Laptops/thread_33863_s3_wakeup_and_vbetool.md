---
title: "s3 wakeup and vbetool"
date: 2005-05-12
forum: Hardware &amp; Laptops
---

### Post by craigmaloney on 2005-05-12
Hi all.

I've been trying to get suspend-to-ram working on my laptop (Dell x200 Intel i810 based).  I love it 'cause it's 2.9 lbs.  I hate it 'cause of all this suspend-to-ram bull.  (and there's some problems working with getting my hfs+ ipod to work)

I can use vbetool a'la'carte from the console (not associated with a wakeup cycle) and it seems to work ("vbetool post" doesn't kill things) so long as I boot without the vga=771 kernel parameter (which the hoary install put in the grub config).

Anyway, my question is 2 fold.

1) I lose the keyboard after wakeup (numlock doesn't do anything), but the backlight comes back on.  No video visible.  Should I still presume this is a video POST-ing problem (i810 is also in charge of console?), or does the loss of console mean it's something more insidious?  That is: since "vbetool post" works when it's not in the context of wakingup, is the video POSTing a red herring?

2) My network doesn't come back after wakeup.  There is nothing in the logs which indicates why this happens (the driver isn't supposed to be unloaded, so there wouldn't be anything to look at in the logs, right?)  Basically, does anyone have (newbie) suggestions about how to proceed debugging stuff like this?

Also... since the hoary scripts always want to call vbetool explicitly, the s3_bios and s3_mode kernel parameters should NEVER be used, right?

Much thanks.
--Craig

---

