---
title: "Another G400 Dualhead thread (Breezy)"
date: 2005-09-25
forum: Hardware &amp; Laptops
---

### Post by AndyC_772 on 2005-09-25
New to Linux and just installed the preview version of Breezy... so possibly not the greatest combination in the world ;)

My graphics card is a Matrox G400 Dualhead, and after editing my xorg.conf I can get my primary display to run in 1600x1200x85, which is great. So far, so good.

However, I've spent the last few hours trying to figure out how to get my secondary display to work, and I've come up against a brick wall. Some people report that the G400 works great under Linux, and I'm very happy for them - but I can't see how to enable support for the secondary display under Breezy.

I understand that I need to install the Matrox HAL driver, but I'm not 100% convinced it even supports the right version of Xorg (yet).

Also my screen redraw is rather slow, so I don't believe I have hardware acceleration enabled. Maybe I'm just confirming [this bug](http://www.ubuntuforums.org/showthread.php?t=64666&highlight=dri+g400), or is there something else I should check or set up?

TIA

Andy

---

### Post by jnuts on 2005-10-01
I'm having the same problems.... anybody found a solution yet?

---

### Post by AndyC_772 on 2005-10-06
Not yet :(

---

### Post by darkG20t on 2005-10-10
> **AndyC_772]New to Linux and just installed the preview version of Breezy... so possibly not the greatest combination in the world  said:**
> 

I'm new and using Breezy too.So you're not alone.

[Quote]However, I've spent the last few hours trying to figure out how to get my secondary display to work, and I've come up against a brick wall. Some people report that the G400 works great under Linux, and I'm very happy for them - but I can't see how to enable support for the secondary display under Breezy.

Did you search and try this post?
[http://www.ubuntuforums.org/showthread.php?t=23628&highlight=nvidia+tv]("http://www.ubuntuforums.org/showthread.php?t=23628&highlight=nvidia+tv")
It took me a few days of fooling around, but I got dual monitors working with a CRT and my TV via svideo (I have a GeForce 5200). This may not be exactly what you need but I bet it will point you in the right direction.

Also, don't forget to open up your breezy to install packages via the 'apt-get' command. Everything was much easier once I did that. Instructions can be found on the starters guide: [http://www.frankandjacq.com/ubuntuguide/5.04/index.html#extrarepositories]("http://www.frankandjacq.com/ubuntuguide/5.04/index.html#extrarepositories")

---

### Post by AndyC_772 on 2005-10-11
Thanks for the suggestions, but unfortunately the G400 is a bit of a special case, in that (I believe) it requires the Matrox HAL driver which is binary-only and doesn't seem to support the latest x.org. I suspect the most straightforward answer might just be a new graphics card or two :(

---

### Post by metallmann on 2005-11-20
[QUOTE=AndyC_772]Thanks for the suggestions, but unfortunately the G400 is a bit of a special case, in that (I believe) it requires the Matrox HAL driver which is binary-only and doesn't seem to support the latest x.org. I [/QUOTE]

Mmm.. did you check [http://www.matrox.com/mga/support/drivers/latest/home.cfm](http://www.matrox.com/mga/support/drivers/latest/home.cfm)
I see a  Matrox Marvel G400-TV and a  Matrox Millennium G400 / Matrox Millennium G400 MAX on the far bottom of the list..

I had the same problem with my Matrox G550. Could only get the second head working when I first started in a "single screen" mode and then copied the right xorg.conf back and restarted gdm.

I've been having this problem some months now, and I sort of hoped the problems would go away with an upgrade to "breezy badger".. alas..
BUT...  I reread some comment on the freedesktop bugzilla list from 2004-10-17 and decided to try that again ([https://bugs.freedesktop.org/show_bug.cgi?id=615](https://bugs.freedesktop.org/show_bug.cgi?id=615))
I got the source from the latest driver page of the matrox-site ([http://www.matrox.com/mga/support/drivers/latest/home.cfm](http://www.matrox.com/mga/support/drivers/latest/home.cfm)) fitting to my system (AMDK6 - [http://www.matrox.com/mga/support/drivers/files/lnx_42.cfm](http://www.matrox.com/mga/support/drivers/files/lnx_42.cfm)) and installed it. (it even got a installscript; just like windows :)) )
Fixed a workaround of the previous driver and  I got liftof!

---

