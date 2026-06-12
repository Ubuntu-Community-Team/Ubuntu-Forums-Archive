---
title: "Intel 945GM -- updated Xorg driver?"
date: 2008-07-28
forum: Hardware
---

### Post by xi0nic on 2008-07-28
Hello,

  A search of the forums didn't turn up any information, so I'm hoping someone here can help me.

  I'm trying to find out if I can get a newer version of the intel driver for my machine. My Ubuntu install seems to be running a two year old driver, and I can't find if there's a newer one anywhere.

  Relevant output from glxinfo:
```
OpenGL renderer string: Mesa DRI Intel(R) 945GM 20061017 x86/MMX/SSE2
OpenGL version string: 1.3 Mesa 7.0.3-rc2
```

Thanks in advance!

---

### Post by NoFearDJB on 2008-07-28
> **xi0nic said:**
> Hello,

  A search of the forums didn't turn up any information, so I'm hoping someone here can help me.

  I'm trying to find out if I can get a newer version of the intel driver for my machine. My Ubuntu install seems to be running a two year old driver, and I can't find if there's a newer one anywhere.

  Relevant output from glxinfo:
```
OpenGL renderer string: Mesa DRI Intel(R) 945GM 20061017 x86/MMX/SSE2
OpenGL version string: 1.3 Mesa 7.0.3-rc2
```

Thanks in advance!

My glxinfo:
```
OpenGL renderer string: Mesa DRI Intel(R) 915GM 20061017 x86/MMX/SSE2
OpenGL version string: 1.3 Mesa 7.0.3-rc2

```
I think that even though its dated as 2006, there hasn't been any major updates that have been necessary. If there were some updates, Ubuntu would notify you via package manager like anything else. Are you having some problems that sparked your search for something new?

---

### Post by xi0nic on 2008-07-28
I haven't had any serious issues, I'm just on a mission to get WoW+Wine to work with this chipset. I can play in Windows just fine, so I know it's got to be possible!

---

