---
title: "[wubi] How can I launch Ubuntu from Win?"
date: 2009-02-24
forum: Installation &amp; Upgrades
---

### Post by chubble10 on 2009-02-24
:!: How can you disable the boot menu when Windows starts up, and only launch Ubuntu through Windows?

P.S. I want to use Wubi, or can I use the Live CD Install, but still have no boot menu appear?

Phil :!:

---

### Post by avtolle on 2009-02-24
If you do a Wubi install, you will get a boot screen from the Windows side allowing you to select either Windows or Ubuntu (w/Windows as a default). It is my understanding that you may reverse these, but as to eliminating the appearance of Windows as an option, I don't know how you would do this. I'm sure there may be a way, but I don't know what it is (not really understanding why you want to do this).

---

### Post by chubble10 on 2009-03-08
> **avtolle said:**
> If you do a Wubi install, you will get a boot screen from the Windows side allowing you to select either Windows or Ubuntu (w/Windows as a default). It is my understanding that you may reverse these, but as to eliminating the appearance of Windows as an option, I don't know how you would do this. I'm sure there may be a way, but I don't know what it is (not really understanding why you want to do this).

I want to be able to double-click on an icon on my Windows desktop and it will launch Ubuntu

---

### Post by thymox on 2009-03-12
You could try **loadlin** or even having a play around with **grub4dos**.  Both of these can boot a Linux system from within Windows, but if the system is a WUBI-based one, you may have to fiddle a bit to get the right options.

Good luck. :)

---

