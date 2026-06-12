---
title: "upgrade to 9.04 kills grub?"
date: 2009-08-06
forum: Installation &amp; Upgrades
---

### Post by tudor_victor on 2009-08-06
hello,
I had a dual boot running with windows XP and ubuntu (the last version before 9.04)

I upgraded to 9.04 using synaptic and after the upgrade completed, I can't boot ubuntu anymore, only windows.

does upgrading to 9.04 from synaptic affect grub as well? how do I restore my dual-boot now?

---

### Post by stlsaint on 2009-08-06
try booting to a livecd and repair grub or post what grub says after you use the /grub/boot/menu.lst! 
(if you arent sure what i mean by this than please dont use and just post what you need help with)! DO NOT USE IF YOU DONT KNOW WHAT YOU ARE DOIN! seek and you shall find.

---

### Post by tudor_victor on 2009-08-06
> **stlsaint said:**
> try booting to a livecd and repair grub or post what grub says after you use the /grub/boot/menu.lst! 
(if you arent sure what i mean by this than please dont use and just post what you need help with)! DO NOT USE IF YOU DONT KNOW WHAT YOU ARE DOIN! seek and you shall find.

I booted from liveCD and I don't see my old filesystem anymore (looked for it in gparted)

I see all hard drives except the one where linux was installed.

WTF?

---

### Post by merlinus on 2009-08-06
Post results of
```

sudo fdisk -l
```

---

