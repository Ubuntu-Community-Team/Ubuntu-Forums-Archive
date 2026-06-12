---
title: "Will Feisty support Intel Santa Rosa? (X3100 gfx, i4965 Wifi)"
date: 2007-08-12
forum: Hardware &amp; Laptops
---

### Post by christian.convey on 2007-08-12
I just bought a Dell D830.  It's got Intel an X3100 graphics chip, and an Intel 4965 wifi chip.

Neither of these seems to be supported in Feisty, and I can't yet get Gutsy booting this laptop.

Does anyone know if/when the drivers for these two devices will be backported to Feisty?  If they already have, how to I get access to them?

Thanks,
Christian

---

### Post by christian.convey on 2007-08-12
Good news.  I found that video basically works when I do this:

sudo aptitude install xserver-xorg-video-intel

My guess is that Feisty's intaller doesn't know about the X3100 chip, but the driver mentioned above now resides in the repositories.

---

