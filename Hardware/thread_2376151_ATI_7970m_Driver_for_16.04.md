---
title: "ATI 7970m Driver for 16.04"
date: 2017-10-30
forum: Hardware
---

### Post by noperative on 2017-10-30
Are there any ATI drivers that work well for a 7970m on 16.04? If so what do I need to search for / check that I have installed? I pulled this hard drive out of a desktop I had an nvidia card in, popped it in my laptop and just removed all of the nvidia drivers.

---

### Post by Yellow Pasque on 2017-10-31
The correct drivers should already be loaded by default. Check glxinfo to verify:
```
glxinfo | grep string
```
If you see "Gallium 0.4 on AMD <something>", you are good to go.

---

