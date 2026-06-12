---
title: "USB mp3 player not recognized"
date: 2008-03-26
forum: Hardware &amp; Laptops
---

### Post by Grone1985 on 2008-03-26
So, my mp3 player stopped being recognized after a "possible" unsafe removal, I say possible because I'm not sure that it actually happened, but someone told me that could have happened to them. It's a sansa c250 and I'm running on Gutsy AMD64.

Anyone can help?
Thanks!

---

### Post by Sadist on 2008-03-27
open terminal and type

```
sudo modprobe usb-storage
```

and plug in player

---

### Post by Grone1985 on 2008-03-27
> **Sadist said:**
> open terminal and type

```
sudo modprobe usb-storage
```

and plug in player

Thanks dude! That worked! :guitar:

---

