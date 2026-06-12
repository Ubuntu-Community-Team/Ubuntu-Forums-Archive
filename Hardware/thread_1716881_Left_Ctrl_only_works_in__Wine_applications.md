---
title: "Left Ctrl only works in  Wine applications"
date: 2011-03-29
forum: Hardware
---

### Post by Wtwine on 2011-03-29
Hi

I run my PC on Ubuntu 10.10 

The left ctrl key on my computer stopped working (I checked it on Windows machines to make sure it was a hardware problem).  I remapped the left Control key to left Super key (keycode 133) by adding the following to my /etc /rc.local and etc/X11/Xsession files:

```
xmodmap -e 'keycode 133 = Control_L NoSymbol Control_L' -e 'clear Control' -e 'add Control = Control_L Control_R'
```

Now the Super_L works as Ctrl_L in applications running in Wine and in my Windows XP virtual machine, but not in applications running natively in Ubuntu!  I have checked for issues in key bindings in Compiz, sticky keys in keyboard accessibility, and" show position of pointer" in mouse accessibility, and there are no incompatibilities there.

I use left Ctrl A LOT (Ctrl_c, Ctrl_v, Ctrl_x, and for opening as new tab in Firefox), and I also use Caps Lock so I don't want to swap the Caps Lock and the broken Ctrl_L key, as you can do in keyboard options.

Any suggestions?

Thanks

---

