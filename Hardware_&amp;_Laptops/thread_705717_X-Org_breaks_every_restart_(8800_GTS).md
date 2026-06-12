---
title: "X-Org breaks every restart (8800 GTS)"
date: 2008-02-23
forum: Hardware &amp; Laptops
---

### Post by goorioles747 on 2008-02-23
I have an 2x 8800 GTS 320 mb cards running in SLI. I have tried installing nvidias lastest driver off of their site and Envy's automated installer. Both work fine until i restart my computer. Then I have to boot into recovery mode and replace x-org with my .backup which allows it to boot but leaves it without a video driver again...

I searched and found other people with a similar problem but couldnt find any answers that worked.

---

### Post by patrickfromspain on 2008-02-23
You must uninstall the linux-restricted-2.6.22-14-generic package or disable the nvidia module that's in it. 

Hope that helps!

---

