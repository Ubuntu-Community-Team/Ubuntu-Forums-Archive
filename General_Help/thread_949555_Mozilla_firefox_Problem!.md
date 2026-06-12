---
title: "Mozilla firefox Problem!"
date: 2008-10-16
forum: General Help
---

### Post by LidanJericho on 2008-10-16
I've just now download Adobe Flash Player 10 and when i try to install it (from the terminal) 

it's say this error:
"NOTE: Please ask your administrator to remove the xpti.dat from the
components directory of the Mozilla or Netscape browser."

where this file and it's ok to delete it?

Thanks.

---

### Post by Sam on 2008-10-16
To find out where the file is:```
locate xpti.dat
```
If you are not sure about deletion, the better is to rename it or move it elsewhere, then check if it works, and if it broke something, just revert what you done.

BTW, you can get a debian package of Flash 10 [here](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&promoid=DXLUJ)

---

