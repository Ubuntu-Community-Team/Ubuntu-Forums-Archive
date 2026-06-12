---
title: "Screen position on laptop"
date: 2006-12-02
forum: Hardware &amp; Laptops
---

### Post by MaJoR42 on 2006-12-02
I've been banging my head on this one for a few days.

I've installed Ubuntu 6.06 on my HP Omnibook 500. Everything seems to have autodetected OK, except that the X screen is positioned about 1 millimetre too high on the laptop display. It's an ATI internal AGP graphics card.

If I adjust the position using xvidtune, it can be adjusted to the right position.

I then generated a modeline, and put that in the monitor section of xorg.conf.

I can see my xorg.conf file getting loaded in the log file, but the defaults from the ATI module seem to be the ones getting loaded, and my modeline is being ignored.

Can anyone help? There's been a lot of traffic on similar issues, but nothing appears to work for me...  ](*,)

---

### Post by MaJoR42 on 2007-01-07
Just for closure: I never did find a solution in dapper. I upgraded to 6.10 Edgy Eft, and the display is perfectly aligned.

Now if I can only get the Omnibook extensions module compiled... ;)

---

