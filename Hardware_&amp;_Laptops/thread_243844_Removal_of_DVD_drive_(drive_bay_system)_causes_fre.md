---
title: "Removal of DVD drive (drive bay system) causes freeze"
date: 2006-08-25
forum: Hardware &amp; Laptops
---

### Post by _profox on 2006-08-25
I have an IBM Thinkpad T40.

There is a drive bay with a DVD drive in it.

In windows xp I used to be able to eject the DVD drive out of the drive bay and insert another one - while the operating system is still running - This was extremely handy for me, because I have an extra CD-R drive that does not read DVD's but is able to burn CD's :)

I'm too cheap to buy a new DVD-R combo drive ;) and I just want to know more about this issue...

I know the technique of changing the drive is called hotswapping.

Anyone with more information/links is very welcome :)

thanks guys :KS

[B]edit: fixed by compiling lt_hotswap and putting it in /etc/modules and adding the option "auto_eject=1" in /etc/modprobe.d/options

need more info? just ask :)[/B]

---

### Post by _profox on 2006-08-25
Hello guys! I found this: [http://www.thinkwiki.org/wiki/How_to_hotswap_UltraBay_devices](http://www.thinkwiki.org/wiki/How_to_hotswap_UltraBay_devices)
And I will investigate it :)

---

### Post by _profox on 2006-08-25
This looks nice to me:

[http://www.thinkwiki.org/wiki/Lt_hotswap](http://www.thinkwiki.org/wiki/Lt_hotswap)

Can I request for it to be included by default in Edgy somewhere ? :)
Or atleast in the repositories ? :)

There's also the generic "hotswap" available in the repositories, but it has kernel problems with 2.6 that cause DMA to get disabled after a drive gets re-inserted...

Thanks!

---

