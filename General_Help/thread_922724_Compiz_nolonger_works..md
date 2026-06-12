---
title: "Compiz nolonger works."
date: 2008-09-17
forum: General Help
---

### Post by mummim on 2008-09-17
I am using Ubuntu, the latest update (8.04). Lately, I have some problems with compiz. It just suddenly stops working.
I can still access the "Advanced desktop effects settings" window and change the effect, but nothing happens after that.
I can still change some effect through Appreance Preferences >> Visual affect (from none to normal or Extra).
I have tried to reinstall compiz config, and compiz packages.

I have tried compiz-test and have the following result:

[INDENT]```
 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]
```[/INDENT]

I have searched but couldn't find any more information. Please help me out, I really love those effects.

---

### Post by mummim on 2008-09-24
I have found out the problem. For some reason, compiz doesn't autostart when the OS boot. IT works well when I started manually , by the command "compiz".

If anyone has the same problem, she/he may edit the startup list.

Thanks for your attention. Sorry for bothering you so much in such a small problem though.

---

