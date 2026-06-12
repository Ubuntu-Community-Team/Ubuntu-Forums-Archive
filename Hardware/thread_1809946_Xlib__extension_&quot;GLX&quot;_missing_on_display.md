---
title: "Xlib:  extension &quot;GLX&quot; missing on display &quot;:0.0&quot;."
date: 2011-07-22
forum: Hardware
---

### Post by Ddorda on 2011-07-22
Hey guys,

I've just installed Ubuntu 11.04 on my PC.
On the first boot I got an error about Unity cannot load.

when I tried running games or compiz I got the error (or similar to):
```
Xlib:  extension "GLX" missing on display ":0.0".
```

from lspci:
```
01:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]
01:00.1 Display controller: ATI Technologies Inc RV370 [Radeon X300SE]

```

After a research I found that my Video card is supposed to be supported by the kernel ([https://help.ubuntu.com/community/RadeonDriver#Accelerated%203D%20support](https://help.ubuntu.com/community/RadeonDriver#Accelerated%203D%20support) )


Thanks!

---

### Post by i.r.id10t on 2011-07-22
You need to install the fglrx x server package

---

