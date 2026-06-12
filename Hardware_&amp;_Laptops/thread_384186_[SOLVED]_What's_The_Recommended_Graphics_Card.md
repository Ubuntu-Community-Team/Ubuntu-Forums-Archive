---
title: "[SOLVED] What's The Recommended Graphics Card?"
date: 2007-03-14
forum: Hardware &amp; Laptops
---

### Post by AlistairH on 2007-03-14
I recently bought a new pc with a Foxconn motherboard and SiS chipsets. Specifically, this mobo has SiS Mirage integrated graphics which, from what I gather in various threads, is not the best as far as Ubuntu is concerned.

The problem that I'm getting is a limited screen resolution - 1024 x 786 max. Not good.

Like a few others, I've had great difficulty finding Linux drivers for this display so I've decided to purchase another graphics card and switch off the on board one.

Can any of you who have already been through the loop recommend a reasonably priced graphics card that is guaranteed to work with Edgy?

I have no need for fancy 3D graphics as I don't play games other than the odd bit of Solitaire. I do however create fantasy art and need the detail that a high resolution brings. An absolute minimum would be 1280 x 1024.

Thanks in advance for your help folks.

Ali

---

### Post by teaker1s on 2007-03-14
before spending any money have you tried reconfiguring display by
```
sudo dpkg-reconfigure xserver-xorg
``` go through sections any you should be able to select a better resolution that can then be used on desktop

other than that nvidia cards well supported if not the latest and greatest model

---

### Post by AlistairH on 2007-03-15
Thanks Teaker, I'll look at that tonight after work.

---

### Post by AlistairH on 2007-03-15
Excellent Teaker. Worked a treat.

You saved me a few bob there. I owe you a beer.

---

### Post by teaker1s on 2007-03-15
welcome:popcorn:

---

