---
title: "Somebody use Tablet PC and Ubuntu?"
date: 2007-06-24
forum: Hardware &amp; Laptops
---

### Post by DouglasCaixeta on 2007-06-24
Hi,

I have a Toshiba Tablet PC (Satellite R15) and I have some problems with Ubuntu.

When I rotate the screen the mouse pointer goes crazy. 
I can move around normal, but when I use the pen, is everything the opposite.

Can I change this somewhere?

Thanks for the repplies

---

### Post by bcw on 2007-06-24
Hello,

The screen is the screen, and the tablet is the tablet - they are separate.

Install the wacom-tools and use xsetwacom to rotate the wacom digitiser when you use xrandr to rotate the screen.

Cheers,
Bret

---

### Post by olejorgen on 2007-07-01
Here is the script I'm using:
```

#!/bin/sh
orientation=`/usr/bin/xrandr --query | /bin/grep "Current rotation" | /usr/bin/awk '{print $4}'`
if [ "$orientation" = "normal" ]; then
/usr/bin/xrandr --orientation inverted
/usr/bin/xsetwacom set stylus Rotate 3
else
/usr/bin/xrandr --orientation normal
/usr/bin/xsetwacom set stylus Rotate none
fi

```

This is only for flipping the screen, but could easily be extended to do portrait mode too

---

