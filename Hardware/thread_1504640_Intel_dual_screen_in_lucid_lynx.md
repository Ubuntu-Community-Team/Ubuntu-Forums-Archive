---
title: "Intel dual screen in lucid lynx"
date: 2010-06-08
forum: Hardware
---

### Post by unavenged on 2010-06-08
Hi... I have a POS pc that i ned to set an extended desktop to have something display on the 2nd screen, the VGA controller is an Intel Corporation 82852/855GM Integrated Graphics Device. Can some one please help me out?

I have tried this aswell [https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes) and [https://help.ubuntu.com/community/XineramaHowTo#Intel%20integrated%20graphics%20adapters](https://help.ubuntu.com/community/XineramaHowTo#Intel%20integrated%20graphics%20adapters)

Here is the output from lshw and lspci:

```
kiosk@kioskplayer:~$ sudo lshw -C video
  *-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: 82852/855GM Integrated Graphics Device
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:d8000000-dfffffff(prefetchable) memory:e8180000-e81fffff ioport:e300(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: 82852/855GM Integrated Graphics Device
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:e0000000-e7ffffff(prefetchable) memory:e8100000-e817ffff

```

```
kiosk@kioskplayer:~$ lspci
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)

```

---

### Post by unavenged on 2010-06-09
Hi... This is more or less the type of POS pc we are using [http://pantallatactil.net/index.php?tpl=ficha&id_idioma=en&id_categoria=5&id_producte=35&desc=Metal%20Panel%20PC%20MPPC-K795](http://pantallatactil.net/index.php?tpl=ficha&id_idioma=en&id_categoria=5&id_producte=35&desc=Metal%20Panel%20PC%20MPPC-K795)

---

### Post by unavenged on 2010-06-10
Bump... I'm still having no luck

---

