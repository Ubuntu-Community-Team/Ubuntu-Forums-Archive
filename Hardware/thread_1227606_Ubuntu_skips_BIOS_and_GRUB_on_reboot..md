---
title: "Ubuntu skips BIOS and GRUB on reboot."
date: 2009-07-30
forum: Hardware
---

### Post by modmadmike on 2009-07-30
When I chose reboot from the shutdown menu Ubuntu unloads itself and then reloads itself (Bypassing the BIOS, and GRUB) at first I though it was a feture but if I don't manually restart (By pressing Reset or power cycling it) the NVIDIA driver does not work and therefore X wont load normally.

---

### Post by komputes on 2009-07-30
I'm sure what I post here won't be much help, but I could confirm this, although I haven't had it in a while and I'm not sure what it is caused by either.
 
 Just throwing out some ideas at what I think might affect it. Maybe it's the nvidia binary driver. If you deactivate it from "System > Administration > Hardware drivers" are you able to restart properly?

---

### Post by modmadmike on 2009-08-13
> **komputes said:**
> I'm sure what I post here won't be much help, but I could confirm this, although I haven't had it in a while and I'm not sure what it is caused by either.
 
 Just throwing out some ideas at what I think might affect it. Maybe it's the nvidia binary driver. If you deactivate it from "System > Administration > Hardware drivers" are you able to restart properly?

Turns out I somehow installed kexec which is designed for speed ing the reboot process but is unfortunately incompatible with the Nvidia binary driver.

---

