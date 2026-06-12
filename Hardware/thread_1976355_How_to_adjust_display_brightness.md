---
title: "How to adjust display brightness?"
date: 2012-05-08
forum: Hardware
---

### Post by pasoleatis on 2012-05-08
Hello,

I have Acer 4830tg laptop with ubuntu 12.04. I am trying to make it run as long as possible on battery, but I can not adjust the brightness. It is always as maximum. I think this would give an extra 30 minutes of battery life. I tried the laptop keyboard control and also the ubunutu settings. None work. How can I change the brightness?

---

### Post by pasoleatis on 2012-06-03
> **pasoleatis said:**
> Hello,

I have Acer 4830tg laptop with ubuntu 12.04. I am trying to make it run as long as possible on battery, but I can not adjust the brightness. It is always as maximum. I think this would give an extra 30 minutes of battery life. I tried the laptop keyboard control and also the ubunutu settings. None work. How can I change the brightness?

After digging some time, I managed to find the answer in this post [https://wiki.archlinux.org/index.php/Acer_Timeline_3830](https://wiki.archlinux.org/index.php/Acer_Timeline_3830). Maybe the solution was so obvious and nobody answered, but maybe if someone with similar problem can find it easier now. Just added to the grub option acpi_osi=Linux acpi_backlight=vendor in the /etc/default/grub (followed by sudo update-grub). The 12.04 has more problems anywax. By accident I found out that using the Ununtu 2D instead of 3D doubled the battery life, while putting the minimum brightness adds almost 2 hours to the battery life (doing nothing).

---

