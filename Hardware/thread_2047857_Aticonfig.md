---
title: "Aticonfig"
date: 2012-08-25
forum: Hardware
---

### Post by filip007 on 2012-08-25
I have manually install latest driver, i put make and gcc on to get started, everything works but i like to enable PowerXpress.

If i use this **aticonfig --px-igpu** it wants restart, and when i do logout and check again it's again in (High-Performance mode) not (Power-Saving mode)?

Edit:
Well actually is (Power-Saving mode), without restart when i use that command but if i open Catalyst Control Center it switches back to (High-Performance mode). 

**Can someone build a tray tool, for picking in what mode GPU will be running that would be great, if possible maybe i'm wrong here.**

aticonfig --px-igpu (enabled power saving)

aticonfig --px-dgpu (enables high performance)

aticonfig --pxl (status check)

Still not sure if this is active or not...?
Xsensors app don't show GPU temp any more with this newer driver?

Can't put my lips on that...

---

