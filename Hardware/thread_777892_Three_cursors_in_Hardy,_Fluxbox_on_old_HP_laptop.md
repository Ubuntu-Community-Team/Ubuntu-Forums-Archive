---
title: "Three cursors in Hardy, Fluxbox on old HP laptop"
date: 2008-05-01
forum: Hardware
---

### Post by dafyddhughes on 2008-05-01
Hi there

I've just upgraded to Hardy from Feisty on an _old_ HP Omnibook XE2 (P2 333, 128 Mb I think). Running a really minimal install worked fine with Fluxbox before the upgrade, and it seems pretty good now, except for the fact that my mouse cursor now appears as 3 cursors, repeated first about 15 pixels then about 40 pixels to the right of the real one.

Anybody seen this?

Thanks for any advice.

cheers
dafydd

---

### Post by Paradoxdruid on 2008-06-09
I just did a series of upgrades on my old Acer Tablet PC running Kubuntu Gutsy, and when I upgraded to Feisty, I got the same thing--  three mouse cursors showing, just as you describe.  I hoped it was just an upgrade bug or something, and proceeded with the next upgrade from Feisty to Hardy.

Unfortunately, this behavior is retained in Hardy on the acer tablet.  I'm pretty lost as to what could be causing it.

Interestingly, if I change my cursor theme, the normal arrow goes to a single cursor, but when I move to, say, a window border, and the cursor changes, it again shows three repeated cursors.

Any ideas, anyone?

---

### Post by dafyddhughes on 2008-06-15
Hey - so I'm not alone!

I think I've figured out that, at least in my case, it's the login manager. I think I switched frm xdm to gdm and the problem disappeared.

Let me know if that works for you...

---

