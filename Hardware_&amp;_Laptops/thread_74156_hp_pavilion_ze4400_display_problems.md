---
title: "hp pavilion ze4400 display problems"
date: 2005-10-11
forum: Hardware &amp; Laptops
---

### Post by zelah on 2005-10-11
even after adding other resolution sizes to the xorg.conf file, 1024x768 is the highest resolution that it'll offer me. is this the highest that my laptop can go? it looked fine running windows XP, but the top/bottom bars and all ubuntu windows/text are very large still. i tried resizeing the bars but they only go down by 1 pixel (to 23). 

[http://img412.imageshack.us/my.php?image=screenshot1hl.png](http://img412.imageshack.us/my.php?image=screenshot1hl.png)

there's a screenshot, does it look odd to anyone else? if this is the largest resolution i can get on my laptop, is there anyway to sidestep that and shrink everything? am i just stuck like this?

any help would be appreciated

---

### Post by nocturn on 2005-10-11
[QUOTE=zelah]even after adding other resolution sizes to the xorg.conf file, 1024x768 is the highest resolution that it'll offer me. is this the highest that my laptop can go? it looked fine running windows XP, but the top/bottom bars and all ubuntu windows/text are very large still. i tried resizeing the bars but they only go down by 1 pixel (to 23). 
[/QUOTE]

If you open a terminal, and type 
```

xdpyinfo |grep reso

```

It will give something like 100x100 or 75x75 (dpi)
Open the fonts control panel, go to advanced (I think) and set the resolution there.

That helped on some of my boxes.

---

### Post by zelah on 2005-10-11
that does help some, thank you!

---

### Post by nrgtek on 2005-11-01
I have this laptop too and am wondering if it is possible to install ATI drivers for this? The default Xorg file reports it as:

Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon 320M (RS200 IGP)"
        Driver          "ati"
        BusID           "PCI:1:5:0"

My defualt install of breezy is very "choppy" and seems like I get window drawing lag when switching between desktops.

---

