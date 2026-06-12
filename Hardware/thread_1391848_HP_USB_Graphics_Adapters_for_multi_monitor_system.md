---
title: "HP USB Graphics Adapters for multi monitor system?"
date: 2010-01-27
forum: Hardware
---

### Post by Olav on 2010-01-27
Hello everybody. Does anyone know whether this USB-to-DVI adapter will work with Ubuntu 9.10 or 10.4, either 32 bits or 64 bits? If not, are there any alternatives?

I am looking to connect three monitors to a laptop when in my office, one by HDMI and two extra (one on each side of the main monitor) via USB. Graphics performance (Compiz, video) needs to be reasonably good on the HDMI connected screen, but it is not as important on the extra screens. I would like to be able to move my terminal windows and some other stuff to those screens. I understand it won't work for games, but I don't play them.

[http://h18000.www1.hp.com/products/quickspecs/13226_na/13226_na.HTML](http://h18000.www1.hp.com/products/quickspecs/13226_na/13226_na.HTML)

[IMG]http://h10003.www1.hp.com/digmedialib/prodimg/lowres/c01665284.jpg[/IMG]

---

### Post by Olav on 2010-01-28
Noone with any experience with this?

---

### Post by ibuclaw on 2010-02-02
All I can find are bits and pieces of information about sisusb and displaylink, and various people having success with those drivers using different, but similar products.

Can't really say much more than that at this current time.

Regards

---

### Post by Olav on 2010-02-03
Thanks for the reply. I guess these adapters are a little new still, so we just have to wait until better support is available.

---

### Post by ibuclaw on 2010-02-03
Had a little more of a dive around, and found the device drivers for them. Poking at the .inf file reveals this in the comments:
```

; DisplayLinkUsb.inf
;
; Installation inf for DisplayLink USB Display Adapters.
;
; Copyright (c) 2003 - 2009 DisplayLink Corp.

```

It's just a standard DisplayLink device - using Universal Displaylink drivers. So using that logic, a success story with one person should be the same for this device too.

Looking up "DisplayLink" and / or "libdlo" has some odd guides here or there, but nothing recent - except for that you need to disable KMS in order for the driver to work. ([citation]("http://lists.freedesktop.org/archives/libdlo/2009-November/000440.html"))

(edit: A deeper look shows that it may be a Composite aware device too - am not sure what effect this may have, but will need to confirm with the lsusb device information).


Regards
Iain

---

