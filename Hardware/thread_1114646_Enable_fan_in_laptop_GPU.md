---
title: "Enable fan in laptop GPU?"
date: 2009-04-03
forum: Hardware
---

### Post by swraman on 2009-04-03
Hi,

Im running Ubuntu on a laptop with a nvidia geforce 7900 GS.  Normally when I use Windows, the fan for the GPU comes on fairly freqently.  But it seems like it never comes on in Ubuntu.

The gpu then overheats, and the entire system runs slow (especially with Compiz running..)

Is there any way to manually turn it on?  I have the Drivers ubuntu recommended me to download.  In the settings (NVIDIA X SERVER Settings) there is no way to conrol the fan.

Thanks.

Raman

---

### Post by swraman on 2009-04-03
I just tried nvclock, but when I run nvclock --fanspeed 50 i get:

adjustment of the fanspeed isn't supported on your type of videocard!

it recognized the card when i do nvcard --info, it brings up a bunch of info about it and such.

---

