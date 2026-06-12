---
title: "ATi 5850 Unsupported Hardware Watermark"
date: 2010-04-06
forum: Hardware
---

### Post by painejake on 2010-04-06
I installed a ATi Radeon HD 5850 and it works great however there is a watermark shown in the bottom right corner saying 'AMD Unsupported Hardware'

Its playing 3D games fine HD video and compiz effects so it seems fine - I just want to get rid of the watermark. Is there any workaround for be-ridding of this annoyance? I read it was something about a config file? However not sure what I need to do about this.

Thanks in advance ;)

---

### Post by ultiva on 2010-04-06
On my moblity radeon 5650 I've used this patch:

```

#!/bin/sh
DRIVER=/usr/lib/xorg/modules/drivers/fglrx_drv.so
for x in $(objdump -d $DRIVER|awk '/call/&&/EnableLogo/{print "\\x"$2"\\x"$3"\\x"$4"\\x"$5"\\x"$6}'); do
 sed -i "s/$x/\x90\x90\x90\x90\x90/g" $DRIVER
done

```

However, I cannot say that it works like it should because colours are messed up - it look like card displays 64K of colours instead of 16mln. Also sometimes framebuffer is blown up by the ati driver.

Whatever, this patch removes watermark :)

---

### Post by painejake on 2010-04-06
Thanks for the reply :)

Hopefully they will support the 5XXX cards in the next driver update ;)

Thanks for the hack. Does compiz and 3D rendering still work ok with it then?

---

### Post by ultiva on 2010-04-06
Yes, after hack on my 5650 compiz and 3d acceleration works as before. Catalyst control center also works OK. On my radeon problem is only with that colour palette, it was also preset before the patch. Gradients looks really like *** :|

---

### Post by painejake on 2010-04-08
Works great on the 5850 thanks :) Can finally see the bottom right of my screen! :)

---

