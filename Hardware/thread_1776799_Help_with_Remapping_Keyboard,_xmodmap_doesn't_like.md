---
title: "Help with Remapping Keyboard, xmodmap doesn't like me"
date: 2011-06-06
forum: Hardware
---

### Post by Camma on 2011-06-06
Can anyone solve this problem for me? 

I would like the remap the following keys

'R_ Ctrl'  to become ' P '

' ¬  '  to become ' Y '

' Caps_Lock '  to become ' N '

' \ ' to become ' H '

' Home ' to become ' -_ '

' page up ' to become ' ?/ '

' Page dwn ' to become ' 6 '

' End ' to become ' 0 ' 

I have tried xmodmap with no luck and i cant seem to get XkeysCaps to Build/Install..
My Laptop is a Toshiba equium a110    .KeyBoard is f***ed.
Thanks

---

### Post by vamped on 2011-06-10
> **Camma said:**
> 
... I cant seem to get XkeysCaps to Build/Install..


I believe xkeycaps is in the repositories, so there is no need to build/install it yourself.

```
$ sudo apt-get install xkeycaps
```

works for me.

Hopefully this helps get you on your way to solving your unusual customization.

---

