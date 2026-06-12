---
title: "Resolution problem: 1280x800 on a 15.4&quot; monitor"
date: 2006-06-05
forum: Hardware &amp; Laptops
---

### Post by Morbett on 2006-06-05
I've been trying to figure out how to change my Dell Inspiron 1300's resolution to 1280x800.  

The highest resolution I can choose in System->Prefs->Screen Resolution is 1024X768.

When I do
  
sudo dpkg-reconfigure xserver-xorg 

I can't seem to select 1280x800 in the list.  Does anyone know what I can do to change my resolution?

Thanks.

---

### Post by lcg on 2006-06-05
[QUOTE=Morbett]I've been trying to figure out how to change my Dell Inspiron 1300's resolution to 1280x800.  

The highest resolution I can choose in System->Prefs->Screen Resolution is 1024X768.[/QUOTE]
Does it use an integrated Intel graphics card? Then have a look at 915resolution, that should give you the missing resolutions.

HTH,
Lars

---

### Post by citronelu on 2006-06-05
I have an Acer Aspire 1362WLMi (Nvidia FX Go 5200). I had to manually modify xorg.conf, and add a custom Modeline. I set my display to work at 1280x800 @ 50Hz. To generate the correct modeline use gtf:
```
gtf 1280 800 50 -x
```

---

