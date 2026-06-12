---
title: "jaunty 9.04 media sd card reader not working"
date: 2009-12-14
forum: Hardware
---

### Post by timcredible on 2009-12-14
just bought a new hp p6270z.  everything works except media card reading.  even the media cards in my usb-connected printer don't work (the card reader in the printer worked on my old pc with jaunty).  i tried 9.10 karmic live cd, and the card readers work (both the internal and printer).  however, i tried 9.10 when it came out and i just hate it.  so, does anyone have any ideas what i can do to stay with 9.04 and still get my card readers to work?  i do notice a message on boot with 9.04 about unable to load some module.depend file or something like that but goes by too fast.  should i try the newest kernel in the 9.04 repo?  or try some other upgrade in the 9.04 repo?  

thanks.

---

### Post by timcredible on 2009-12-14
found the answer at [http://ubuntuforums.org/archive/index.php/t-250856.html](http://ubuntuforums.org/archive/index.php/t-250856.html)

```

modprobe tifm_sd

```
and make sure to put the above line in /etc/modules so it works every time

---

### Post by timcredible on 2009-12-20
the above didn't really fix it - the media card reader would work if i had plugged in a flash drive first - weird.  anyway, the real solution was here:
[http://ubuntuforums.org/showpost.php?p=7312473&postcount=5](http://ubuntuforums.org/showpost.php?p=7312473&postcount=5)

---

