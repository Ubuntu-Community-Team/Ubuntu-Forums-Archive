---
title: "Missing printer driver : extracting PPD from Mac drivers?"
date: 2014-01-25
forum: Hardware
---

### Post by renaud2 on 2014-01-25
Hi folks, thanks for reading!

Just bought a (wonderful) [Brother MFC-J6920DW]("http://welcome.solutions.brother.com/BSC/public/us/us/en/model_top/colormfc/mfcj6920dw_us_eu_as.html?reg=us&c=us&lang=en&prod=mfcj6920dw_us_eu_as") (mostly for its networking/social capabilities), but there's no Linux support. Of course, the printer is Google Cloud Print enabled, but I would prefere a native support!

I'm a linux user for years, but I'm really new to CUPS (never had to struggle with a printer until this one!).

1- Since the Mac OS X drivers are available, I was wondering if I could extract the PPD from it to feed my Ubuntu? 

2- If possible, how to find that damned PPD in that HFS image? I already tried to mount and extract those ".dmg" files (using dmg2img and hfsplus), but there's only a bunch of pkg files inside (xar archive), no PPD at all.

Any help appreciated!

---

### Post by cmoman2 on 2014-02-02
I've just bought the same printer and found your post.
I followed these instructions
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html)

If you just want the ppd file it will get installed here.
/usr/share/cups/model/Brother/brother_mfcj6920dw_printer_en.ppd

---

### Post by renaud2 on 2014-02-03
> **cmoman2 said:**
> I've just bought the same printer and found your post.
I followed these instructions
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html)

If you just want the ppd file it will get installed here.
/usr/share/cups/model/Brother/brother_mfcj6920dw_printer_en.ppd

Thanks!

---

