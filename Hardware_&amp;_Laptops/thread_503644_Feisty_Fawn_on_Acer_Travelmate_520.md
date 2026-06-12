---
title: "Feisty Fawn on Acer Travelmate 520"
date: 2007-07-18
forum: Hardware &amp; Laptops
---

### Post by garionw on 2007-07-18
I've been trying to get Ubuntu 7.0 to run on my old Acer Notebook just for fun. However I haven't been able to get it to run at all. I've had a look through the help files, and this is what I've found:

> Use acpi=off to avoid install hang.

Now I presumed that this meant press F6 when booting the live CD, goto the start of the line and enter:
```
acpi=off 
```

But if I enter either that or nothing at all, the most I get is a blank screen with a flashing cursor at the top. Can you boot it from the Live CD at all, or it is just not possible on that older laptop.

I tried using 6.10, and it will load the cursor and the default wallpaper, but even that took ten minutes and then just froze on me.

My harddrive is completely blank too, if that matters at all.

Thanks for your help
 - **Garion**

---

### Post by happy-and-lost on 2007-07-18
you place the acpi=off at the *end* of the kernel line, not the beginning. Oh, and delete the splash and quiet options, so you can see what's going on as it boots.

---

