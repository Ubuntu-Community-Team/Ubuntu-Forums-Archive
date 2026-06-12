---
title: "noisy GeForce GTS 250 Dark Knight"
date: 2010-09-28
forum: Hardware
---

### Post by alexserna on 2010-09-28
Hi,

I have a GeForce GTS 250 Dark Knight but I can't make nvclock to work with it. The fan is making too much noise and I want to lower the speed.

I'm using Ubuntu 9.10 and nvidia driver version 256.53

I downloaded the latest version nvclock0.8b4, did the
```
 ./configure --disable-nvcontrol
  sudo make
  sudo make install 
```process  and nvclock doesn't recognize the card.

I have done nvclock -f -F 40 and I get
 ```
Error: Your card doesn't support fanspeed adjustments!

```Did anyone manage to make it work? Is yours silent or is it a combine harvester like mine?

Hope you can help me...
Thanks

---

