---
title: "Shell commands to move monitors"
date: 2010-12-21
forum: Hardware
---

### Post by threepot on 2010-12-21
Hello Ubuntu Folk :)

I would like to use a shell script to move my 2nd monitor around.
Reason being I sometimes setup on the left, and sometimes on the right. My pc id using an Ati 9500 card if it makes any difference.

Already have a script on my startup list which adds the correct resolutions to my list and then chooses the correct ones, but I'd like to know how to move the layout around.

I'm on a 10.10 ubuntu install (and I love it!! rip windows)

Best wishes to all,

Matt

---

### Post by TSJason on 2010-12-21
Something like this should probably work:

```
xrandr --output VGA --auto
xrandr --output VGA --left-of LVDS
```

or likewise:

```
xrandr --output VGA --auto
xrandr --output VGA --right-of LVDS
```

And then to remove the extended screen:


```
xrandr --output VGA --off

```

---

### Post by threepot on 2010-12-22
Oh yes! That is just the puppy, my output names were a little different but it works a treat.

> xrandr --output VGA-0 --left-of DVI-0

Thank you Jason, that is just perfect. Cheers!

---

### Post by threepot on 2010-12-22
I love the Ubuntu Community.

---

