---
title: "HP-TC1100 stylus loses orientation when screen rotated"
date: 2008-08-21
forum: Hardware
---

### Post by olaoni on 2008-08-21
I am currently experiencing a problem with the orientation of the stylus on my tc1100. 
When the screen is in the normal position the stylus works beautifully, I can even use the stylus as a mouse etc.

The problem occurs when I rotate the screen at this point the stylus loses orientation. 

Below is the script which I am using for achieving the screen rotation.
```


if [ -n "$(xrandr | grep 768x1024)" ]; then
        xrandr -o normal
        xsetwacom set "stylus" Rotate NONE
else
        xrandr -o left
        xsetwacom set "stylus" Rotate CWW
fi

Many thanks for your help.


```

---

