---
title: "Suspend Problems with the Intel950"
date: 2006-05-14
forum: Hardware &amp; Laptops
---

### Post by charles.figura on 2006-05-14
So I got my new Dell D620 friday and installed Dapper.  It's got a Intel 950 graphics adapter and the WXGA+ 1440x900 display.

So - I've installed the 915resolution package and configured a viewmode for 1440x900.  Also added a 24bit mode in my xorg.conf, and set xorg to use the i810 driver.

The good news - graphics acceleration is great.  glxgears is giving me 1800 frames per second (I know, it's not a great benchmark, but it's a decent idea) - much better than I'd ever seem from a laptop.

The problem - I can't suspend to disk.  Or, rather, I can't recover from a suspend.  If I try to supend, the video display does not come back on recover - seems as if the backlight isn't even coming on.  

As a minor note, most of the GL screensavers aren't working right either.  They show up on the upper half or third of the screen, leaving the lower portion completely dark.

I suspect that these two problems share a common cause.

Has anyone with the 950 and the 1440x900 display encountered this problem?  Any ideas?

Thanks -

Charlie

---

### Post by charles.figura on 2006-05-14
Okay - I think I've got part of the problem solved (the most important part).  OPaul made this recommendation in a different post - [http://www.ubuntuforums.org/showthread.php?t=174444](http://www.ubuntuforums.org/showthread.php?t=174444)

[QUOTE=OPaul]Try turning DPMS off.

Add ```
Option         "DPMS"    "false"
``` to the Monitor section of your xorg.conf file.[/QUOTE]

Okay, I didn't set DPMS false, I just commented the DPMS line out.  After doing this, my suspend seems to work just fine.  The GL screensaver is still wonky, but then, if I'm not looking at it, I'm not as concerned.

So DPMS takes care of monitor  power control, yes?  So am I losing anything in shutting down DPMS?

---

