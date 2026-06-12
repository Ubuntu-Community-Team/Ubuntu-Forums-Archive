---
title: "Radeon Mobility HD 2400 and Screen Rotation"
date: 2008-10-08
forum: Hardware
---

### Post by krinderlin on 2008-10-08
I have a convertable gateway C-140x.  For now, to use it as a tablet, I have to stick to landscape mode and use a book to prop up the "front" of my laptop so I can get a decent writing angle.

I'd love to be able to rotate my screen, even if it was just a vertical flip.

About 3 months of internet digging has finally lead me to the conclusion that there is no way for 90% of video cards from ATI and xrandr to cooperate.

I have even tried getting swapped over to the radeonhd driver and I still cannot rotate my screen.

So, I decided to pose the Ubuntu community a question that I've yet to find asked in the forums.

Since there appears to be no way to handle this at a lower level, is there someway to handle a screen flip at a purely software level?  Since I'd be using a pen, I might have to invert the mouse inputs also.

I was just thinking that since there are so many people with ATI graphics biting them in the butt, maybe someone invented a work around that bypassed the drivers completely.

---

### Post by schmolch on 2008-10-11
Im using Tablet-PCs myself but im  not familiar with the current situation of radeon cards regarding rotation.

It might be possible to use the generic vesa driver and do some very slow software rotation.

What you should do is:
- ask this on the xorg mailing list
- Have both Hardy and the latest Intrepid installed so you can try latest versions of drivers
- file bugs at bugs.freedesktop.org (xorg) and bugs.launchpad.net (ubuntu)

good luck!

---

### Post by krinderlin on 2008-10-11
@schmolch: Thanks for the direction.  From what I understand there are several long standing bug reports with the exact same error text as me.  I won't burden the administrators with yet another duplicate bug.  However, I will definitely hit up the mailing list and see if I can get any information on workarounds.

---

