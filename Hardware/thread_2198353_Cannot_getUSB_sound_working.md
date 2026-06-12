---
title: "Cannot getUSB sound working"
date: 2014-01-08
forum: Hardware
---

### Post by Anders J on 2014-01-08
I have one of these small Intel "Next Unit of Computing" boxes and this works perfect running ubuntu.based Mint 16/Cinnamon, using two large Samsung 2560 x 1440 LCD screens via DisplayPort.

However, there is no sound connection on the computer nor on the screens, so I am trying a USB sound card deltaco UAC-03, however without any luck,

Entering cat /proc/asound/cards produces

```
anders@anders-Intel ~ $ cat /proc/asound/cards
 0 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0xf7c30000 irq 47
```

I do not know how to get the USB device in the list, any good advice?

---

