---
title: "No window borders with advanced desktop effects"
date: 2008-09-11
forum: General Help
---

### Post by nikkkko on 2008-09-11
I just added a some more memory so I thought I'd check out the advanced effects. 

Everything works fine, (love that spinning cube), but I no longer have any window borders.  What is the most basic, default, brown vanilla theme known to work which I can test before I start installing other stuff?

Thanks

---

### Post by billgoldberg on 2008-09-11
> **nikkkko said:**
> I just added a some more memory so I thought I'd check out the advanced effects. 

Everything works fine, (love that spinning cube), but I no longer have any window borders.  What is the most basic, default, brown vanilla theme known to work which I can test before I start installing other stuff?

Thanks

Press alt+f2 and use this:

```
emerald --replace
```

(note if you don't have emerald installed, install it.

You can download emerald themes on gnome look (under beryl or compiz).

---

### Post by nikkkko on 2008-09-11
Thanks for the quick reply, but I found the solution I was looking for.  I added```
Option "AddARGBGLXVisuals" "True"
``` to my xorg.conf file under the section "Device" and it all works nicely using GTK as the window decorator. (Emerald is an alternative window decorator, isn't it?)

Anyway, for anyone else with this problem and the same graphics setup as me, hopefully this will come up in a search:

 nVidia Corporation NV18 [GeForce4 MX - nForce GPU] (rev a3)

---

### Post by billgoldberg on 2008-09-11
> **nikkkko said:**
> Thanks for the quick reply, but I found the solution I was looking for.  I added```
Option "AddARGBGLXVisuals" "True"
``` to my xorg.conf file under the section "Device" and it all works nicely using GTK as the window decorator. (Emerald is an alternative window decorator, isn't it?)

Anyway, for anyone else with this problem and the same graphics setup as me, hopefully this will come up in a search:

 nVidia Corporation NV18 [GeForce4 MX - nForce GPU] (rev a3)

Yes.

If you see people with transparent or semi-transparent windows decorations or buttons on the left, they are using emerald instead of metacity.

---

