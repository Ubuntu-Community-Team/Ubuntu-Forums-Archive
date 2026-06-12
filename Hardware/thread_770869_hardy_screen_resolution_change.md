---
title: "hardy screen resolution change"
date: 2008-04-27
forum: Hardware
---

### Post by rogier.de.groot on 2008-04-27
My new hardy install's X config is screwed up. After starting supertux I noticed the graphics were really slow, so I checked the X server config, which turned out to be running on the 'vesa' driver, instead of the intel one it should be using. After trying to modify xorg.conf the system just hung (couldn't even switch to text prompt), so I deleted xorg.conf. Now X starts, and is even using the right driver, BUT it's running in a resolution my monitor doesn't support. I've checked the X log file, which correctly states the modes my monitor supports, but for some reason X uses another one anyway. How do I fix this?

---

