---
title: "Jaunty kernel vs F11 kernel"
date: 2009-05-02
forum: Hardware
---

### Post by mariner09 on 2009-05-02
An interesting question came up in my dabblings with Jaunty and F11.  In Jaunty, I can boot the server kernel and see 4gb of memory.  With the PAE kernel in F11, I can only see 3gb of RAM.  The F11 x86_64 kernel sees all 4gb of RAM.

Does anyone know if there's anything different in the Ubuntu server kernel that would allow making use of all 4gb of RAM that may not be in the F11 PAE kernel?

---

### Post by mariner09 on 2009-05-03
I figured out what happened...

With the F11 PAE kernel, I needed to add a mem=4096M kernel append and apparently that was not allowing use of more than 3gb of RAM...

---

