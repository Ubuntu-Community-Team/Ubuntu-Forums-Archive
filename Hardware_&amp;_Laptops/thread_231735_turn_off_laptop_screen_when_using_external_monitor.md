---
title: "turn off laptop screen when using external monitor?"
date: 2006-08-07
forum: Hardware &amp; Laptops
---

### Post by patr547 on 2006-08-07
I've been playing around for a little bit, and with the little bit of knowledge that I have and my great google efforts, I have a xorg.conf set up with two screens so that I am able to work on my external monitor rather than the laptop LCD. However, when I close the laptop lid, the display never turns off. Is there any way to set up the xorg.conf file so that when the laptop lid is shut it turns off the LCD, but continues using the external monitor?

Also, the way it's set up right now, there are two separate displays. Is there a way to set it up so everything is just cloned between the two (the laptop screen is a widescreen and the external is not).

I don't know what versions of everything I have, but I'm using Xorg, Gnome, and the fglrx drivers with Ubuntu dapper

---

### Post by zcal on 2007-11-03
So, I think my problem may be relevant to [this post]("http://ubuntuforums.org/showthread.php?t=598666"), but I'm not really sure since I never used fn+f7 in the past to switch video outputs.

My problem is somewhat similar to patr547's.

I recently installed 7.10 on my IBM ThinkPad R40 and I've been having some display troubles.  With all previous versions of Ubuntu, if I plugged an external monitor into my laptop's VGA port, I could restart X (ctrl+alt+del) and the video output would switch completely to the external monitor while turning off the laptop's display.  7.10 outputs video to the external display, but leaves the laptop's monitor on as well.  Doing so carries its own set of problems, but I don't care about that.  All I want is to be able to turn off one monitor while displaying on the other.

I figure there should be an easy xorg.conf fix for this problem, but I'm not sure because it had always just worked in previous versions without my having to edit the file.  Any ideas?

By the way, the gui for dealing with multiple monitors hasn't been helpful in the least.  I'd rather just edit xorg.conf manually if the fix would be so easy.

---

