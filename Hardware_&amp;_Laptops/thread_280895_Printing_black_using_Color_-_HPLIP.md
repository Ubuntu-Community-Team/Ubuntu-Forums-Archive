---
title: "Printing black using Color - HPLIP"
date: 2006-10-20
forum: Hardware &amp; Laptops
---

### Post by misteral on 2006-10-20
Hello

When I print (anything!) that should just use the black ink, it seems to use the tri-color inkwell. Only found this out when that ink started to get low and all my blacks started coming out red.

This happens with anything - setting OOO to print black, it uses the tricolor. 

I'm fairly certain it's a function of the print driver (OR is it the driver support in kde/kubuntu??)? as printing from OOO on Windows uses just the black inkwell.

Has anyone seen this before?

---

### Post by 11hjpphty76lkjj on 2006-11-08
If you go to [http://localhost:631](http://localhost:631) and change the printer settings you should be able to fix this. Click on printers, then printer options, etc.

---

### Post by Lord Illidan on 2006-11-08
Printers -> Set Printer Options -> Resolution, Quality, Ink Type, Media Type: -> choose color & black and colour cartridge.

Also, to monitor ink levels, run ```
sudo hp-toolbox
```

---

