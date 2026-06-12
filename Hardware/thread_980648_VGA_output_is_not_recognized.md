---
title: "VGA output is not recognized"
date: 2008-11-13
forum: Hardware
---

### Post by orengolan on 2008-11-13
i try to connect my vaio laptop to an lcd-tv.
the fnc+f7 key (video out) is not working so i try using xrandr:

xrandr --verbose --output VGA --mode 1024x768

but nothing happened. when i type xrandr -q i get this:
```
Screen 0: minimum 1024 x 768, current 1368 x 768, maximum 1368 x 768
default connected 1368x768+0+0 (normal left inverted right) 0mm x 0mm
   1366x768       60.0  
   1360x768       60.0  
   1024x768       60.0  
   1368x768       60.0* 

```

it seems like the VGA does not appear.
any idea what should be my next step?

btw, the laptop is vaio vgn-txn27n, with Intel Graphics Media Accelerator 950.

---

