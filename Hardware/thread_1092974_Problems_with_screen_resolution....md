---
title: "Problems with screen resolution..."
date: 2009-03-11
forum: Hardware
---

### Post by mysticaltopher on 2009-03-11
I need to uninstall some drivers for a 8mb Nvidia TNT2 Vanta LT Graphics card?


I ran $sudo apt-get install nvidia-glx-71
and   $sudo apt-get install nvidia-settings

what's the best way to undo this?


And I need to change the refresh rate how do I do that?  Thanks

---

### Post by bazzer on 2009-03-13
"apt-get remove" ...
however - you might or might not be using the driver you installed. Are you wanting to remove it because you can't set the correct resolution?
In any case, you'll want to look at xrandr documentation, but as a starter, look at the output from ```
xrandr -q
```

---

