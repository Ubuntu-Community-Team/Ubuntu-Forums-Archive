---
title: "Unable to change screen resolution"
date: 2007-01-28
forum: Hardware &amp; Laptops
---

### Post by Degeim on 2007-01-28
As the title says, I'm unable to change the resolution of my screen. I'm using Edgy Eft. The laptop model is Dell Latitude 110L, and Cedega says the video card is:

```
Manufacturer: Tungsten Graphics, Inc
Type: Mesa DRI Intel(R) 915GM 20050225
Video RAM: 8mb
AGP Mem Available: N/A
Driver Version: 1.3 Mesa 6.5.1
```

When running xrandr I'm getting the following:
```
[x]@[x]-laptop:~$ xrandr
 SZ:    Pixels          Physical       Refresh
*0   1024 x 768    ( 302mm x 232mm )  *60  
Current rotation - normal
Current reflection - none
Rotations possible - normal left inverted right 
Reflections possible - none
[x]@[x]-laptop:~$ 
```

What can I do to be able to change the resolution?


Thanks,
Degeim

---

### Post by Stemp on 2007-01-28
[915Driver]("https://help.ubuntu.com/community/i915Driver")

Look at 915Resolution

---

