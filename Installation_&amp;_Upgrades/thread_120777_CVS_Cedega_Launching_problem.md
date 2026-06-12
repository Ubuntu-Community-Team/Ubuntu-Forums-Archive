---
title: "CVS Cedega Launching problem"
date: 2006-01-23
forum: Installation &amp; Upgrades
---

### Post by happyponcho42 on 2006-01-23
Are you running under root? Try:
> sudo cvscedega steam.exe

---

### Post by Pulshion on 2006-01-23
I tried to run Steam.exe with cvscedega and this is what i get. 
```
Line 169: Malformed value '"VideoRam" = "256'
Line 174: Malformed value '"AGPVertexRam" = "32'
fixme:win32:PE_CreateModule Load Configuration directory ignored
For language 'en' several language ids were found:
en_US - 0409; en_GB - 0809; en_AU - 0C09; en_CA - 1009; en_NZ - 1409; en_IE - 1809; en_ZA - 1C09; en_JM - 2009; en_ - 2409; en_BZ - 2809; en_TT - 2C09;
Instead of using first in the list, suggest to define
your LANG environment variable like this: LANG=en_US
err:font:ReadFontDir Can't open directory "/usr/X11R6/lib/X11/fonts/truetype/"

```

As far as i understand it wants truetype fonts...im not sure tho and could someone please guide me in right direction
Thanx

---

